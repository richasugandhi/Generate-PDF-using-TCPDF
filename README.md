<?php

require_once('../config/lang/eng.php');
require_once('../tcpdf.php');

ob_start();
for($i = 0; $i<5; $i++) {
	echo 'if'.'</br>';
	
	$pdf = new TCPDF(PDF_PAGE_ORIENTATION, PDF_UNIT, PDF_PAGE_FORMAT, true, 'UTF-8', false);


//$pdf->SetHeaderData(PDF_HEADER_LOGO, PDF_HEADER_LOGO_WIDTH, PDF_HEADER_TITLE.' 001', PDF_HEADER_STRING);

$pdf->SetFont('dejavusans', '', 14, '', true);

$pdf->AddPage();

$html = <<<EOD
<h1>Welcome to <a href="http://www.tcpdf.org" style="text-decoration:none;background-color:#CC0000;color:black;">&nbsp;<span style="color:black;">TC</span><span style="color:white;">PDF</span>&nbsp;</a>!</h1>
<i>This is the first example of TCPDF library.</i>
<p>This text is printed using the <i>writeHTMLCell()</i> method but you can also use: <i>Multicell(), writeHTML(), Write(), Cell() and Text()</i>.</p>
<p>Please check the source code documentation and other examples for further information.</p>
<p style="color:#CC0000;">TO IMPROVE AND EXPAND TCPDF I NEED YOUR SUPPORT, PLEASE <a href="http://sourceforge.net/donate/index.php?group_id=128076">MAKE A DONATION!</a></p>
EOD;

$pdf->writeHTMLCell($html, true, false, true, false, '');
$pdf->Output('C:\xampp1\htdocs\TaskTest\tcpdf\examples\example_001'.$i.'.pdf', 'F');
}


//============================================================+
// END OF FILE
//============================================================+
