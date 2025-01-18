<?php

class Database {
    private $driver;
    private $host;
    private $dbname;
    private $username;

    private $con;

    // Construtor corrigido
    function __construct() {
        $this->driver = "mysql";
        $this->host = "localhost";
        $this->dbname = "cadastro";
        $this->username = "root"; // Usuário sem senha
    }

    function getConexao() {
        try {
            // Formatação corrigida do DSN
            $this->con = new PDO(
                "$this->driver:host=$this->host;dbname=$this->dbname",
                $this->username
            );
            $this->con->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_WARNING);

            return $this->con;

        } catch (Exception $e) {
            // Corrigido ponto-e-vírgula
            echo $e->getMessage();
        }
    }
}


