Document Processing
===================

Here, sort of sites and Linux command are written to process documents

- To slice pdf pages from pdf follow the [answer of the link](https://superuser.com/a/1034450/1237624)

```sh
pdfseparate -f 1 -l 5 input.pdf output.pdf
```
Here, replace `input.pdf` with the pdf which one you would like to slice. And set the desired name in the place of `output.pdf`

- To unite several pdf in one pdf follow the command

```sh
pdfunite x.pdf y.pdf z.pdf result.pdf
```

- To edit pdf use [this site](https://www.pdfescape.com/account/login/?des=oB93D766D2B030A01594B9327F6D66FB4304E0F8382F589BD)

- This is [another site](https://www.pdf2go.com/) which is also a good source to edit pdf in online version. This requires no account, membership to do this.

- Using [this site](https://bigpdf.11zon.com/en/compress-pdf/compress-pdf-to-100kb.php) a pdf size could be reduced to `100 KB`

- To compress pdf from terminal use the following. Source is taken from [here](https://www.journaldev.com/34668/reduce-pdf-file-size-in-linux)

```sh
ps2pdf usag from terminal : ps2pdf input.pdf output.pdf
```
