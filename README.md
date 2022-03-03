#1 -> composer require barryvdh/laravel-dompdf

#2 -> add in config/app.php:

  'providers' add row:
  
  Barryvdh\DomPDF\ServiceProvider::class,

  'aliases' add row:
  
  'PDF' => Barryvdh\DomPDF\Facade::class,

#3 -> add in bootstrap/app.php

$app->singleton(\Barryvdh\DomPDF\ServiceProvider::class);

#4 -> run comand:

php artisan vendor:publish --provider="Barryvdh\DomPDF\ServiceProvider"



###########################################################

Example Usage:

$user = User::find($idUser);

$mes = $this->getMes(session('mesRelEpcto'));

$data = [
    'user' => $user,
    'mes' => $mes
];

$pdf = Pdf::loadView('relatorios.pdf.detEmpacotamento', $data);

return $pdf->stream();
