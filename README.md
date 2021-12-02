# png-to-pdf-add-text-layer-via-ocr
Mac OS: Highlight text in screen shots - find it again

Ready? In case you are travelling with Apple Mac OS ...

! insure that you allready installed xcode !

1. launch Terminal
2. 
In the terminal, copy and paste the following 'instructions' and execute them

1.1 Load Brew

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
1.2 Load Imagemagick
```
brew install imagemagick
```
1.3 Load OCRmyPDF
```
brew install ocrmypdf
```
2. create Automator quick action / service

2.1 Start Automator

2.2 New quick action / service

2.3 Run Schell script
```
for f in "$@"
do 
 /usr/local/bin/convert "$f" "${f%.*}"_pp.pdf
rm $f
done
export PATH=/usr/local/bin:$PATH
for t in "$@"
do 
ocrmypdf "${t%.*}"_pp.pdf "${t%.*}"_ocr.pdf
rm "${t%.*}"_pp.pdf
done
```
2.4 save the whole thing as 'screen png to ocr pdf

[Background Story](https://www.linkedin.com/posts/joergoyen_hazel-automator-ocr-activity-6839579524485709824-DxRs)
