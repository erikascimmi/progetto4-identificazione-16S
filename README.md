# Progetto 4 — Identificazione batterica da gene marcatore 16S rRNA

Identificazione della specie batterica a partire da dati NGS pubblici amplicon
16S rRNA (accession [SRR36601846](https://www.ncbi.nlm.nih.gov/sra/SRR36601846),
isolato *Escherichia coli-10*), con controllo qualità (FastQC), pulizia delle
read (Trimmomatic), unione dei reads paired-end (vsearch) e identificazione
della specie per confronto con database di riferimento (BLASTN, NCBI).

## Cosa contiene

- `osservazioni_qc.txt` — controllo qualità sui dati grezzi e risultato del trimming
- `osservazioni_blast.txt` — merge delle read e interpretazione del risultato BLAST
- `comandi.txt` — comandi da terminale usati (download e pipeline di analisi), per rendere il progetto riproducibile
- i report HTML generati da FastQC (dati grezzi e dati tagliati)
- `SRR36601846_blast_report.txt` — report completo BLASTN (identificazione della specie)

## Risultati principali

La Read 2 (reverse) mostrava una qualità inferiore alla Read 1 verso la fine
della sequenza, un pattern comune nel sequenziamento paired-end. Dopo il
trimming (Trimmomatic), il 76,23% delle coppie è sopravvissuto intatto su
entrambi i lati. Il merge delle coppie con vsearch ha avuto una resa bassa
(4,2%), poiché il trimming ha ridotto la regione di sovrapposizione tra
forward e reverse; le sequenze unite restano comunque di qualità molto alta
(errore atteso medio 0,50).

L'identificazione tramite BLASTN contro il database *16S ribosomal RNA*
(NCBI) ha prodotto un'identità del 99,36% con *Escherichia coli* (E value:
0.0), coerente con l'etichetta originale del campione nel dataset SRA. Il
gene 16S non distingue con piena certezza *E. coli* da alcune specie di
*Shigella*, geneticamente molto vicine — i primi hit del BLAST condividono
infatti identità pressoché identica tra i due generi.
