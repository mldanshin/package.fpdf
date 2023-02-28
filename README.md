# FPDF

Creating a file in .pdf format.  
Contains code from the site http://www.fpdf.org with minor edits.  
The package was created to be able to install via composer, and make edits to the code in one place.  
In particular, there are problems with Cyrillic in the source code, which are eliminated by the manual https://www.cyberforum.ru/php/thread871394.html.  
Two types of fonts "arial" and "arial_bold" are supported.  

In the Error method, a backslash has been added before the Exception class name

    function Error($msg)
    {
        // Fatal error
        throw new \Exception('FPDF error: '.$msg);
    }

## Requirements
- PHP ^8.2
- Composer

## Installation
Add to the file composer.json  

    "require": {
        "mldanshin/package-fpdf": "^1.84"
    }

    "repositories": [
        {
            "type": "vcs",
            "url": "https://github.com/mldanshin/package-fpdf"
        }
    ]

Execute

    composer update

## Using
Full documentation is available on the website http://www.fpdf.org.  
Example of creating a document:

    use FPDF\FPDF;

    $pdf = new FPDF();
    $pdf->AddFont("arial", "", "arial.php");
    $pdf->AddFont("arial_bold", "", "arial_bold.php");
    $pdf->Cell(20, 5, "text");
    $pdf->Ln();
    $pdf->Output($filePath, "F");

## License

Open source software licensed in accordance with [MIT license](https://opensource.org/licenses/MIT).