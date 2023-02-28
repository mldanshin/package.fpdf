# FPDF

Создание файла в формате .pdf. 
Содержит код с сайта http://www.fpdf.org с небольшими правками.  
Пакет создан для возможности установки через composer, и внесения правок в код в одном месте.  
В частности в исходном коде имеются проблемы с кириллицей, которые устранены по руководству https://www.cyberforum.ru/php/thread871394.html.  
Поддерживаются два типа шрифтов "arial" и "arial_bold".

В методе Error добавлен обратный слэш перед названием класса Exception

    function Error($msg)
    {
        // Fatal error
        throw new \Exception('FPDF error: '.$msg);
    }

## Требования
- PHP 8.2 или выше
- Composer

## Установка
Добавьте в файл composer.json  

    "require": {
        "mldanshin/package-fpdf": "^1.0"
    }

    "repositories": [
        {
            "type": "vcs",
            "url": "https://github.com/mldanshin/package-fpdf"
        }
    ]

Выполните

    composer update

## Использование
Полная документация расположена на сайте http://www.fpdf.org.  
Пример создания документа:

    use FPDF\FPDF;

    $pdf = new FPDF();
    $pdf->AddFont("arial", "", "arial.php");
    $pdf->AddFont("arial_bold", "", "arial_bold.php");
    $pdf->Cell(20, 5, "text");
    $pdf->Ln();
    $pdf->Output($filePath, "F");

## Лицензия

Программное обеспечение с открытым исходным кодом, лицензированное в соответствии с [MIT license](https://opensource.org/licenses/MIT).