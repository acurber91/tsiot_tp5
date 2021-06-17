![header](doc/header.png)

# Trabajo Práctico Nº5

Autor:

* Agustín Curcio Berardi

Docente:

* Carlos Pantelides

## Consignas

### Modificación al Master Test Plan

Agregar una característica a determinar al master test plan y desarrollar una acción de test
de un test case sencillo de esta característica.

Se solicita entregar:
- Documento Master Test Plan modificado.
- Documento con el desarrollo de la acción de test.

---

## Solución propuesta

Se implementará una prueba para realizar un análisis estático del código del sensor con el objetivo de encontrar vulnerabilidades. Para ello, se utilizará la herramienta [Bandit](https://pypi.org/project/bandit/) dentro de un entorno de test. Para aislarlo del resto ejecutaremos dicho análisis dentro de un entorno virtual. Instalamos `virtualenv` con el siguiente comando:

    sudo apt install virtualenv
    sudo apt-get install python3-venv

Y luego lo inicializamos:

    virtualenv bandit-env
    python3 -m venv bandit-env
    source bandit-env/bin/activate

Ya inicializado el entorno virtual, vamos a instalar la herramienta en cuestión.

    pip3 install bandit

En esta instancia estarían dadas las condiciones para ejecutar Bandit. Para hacerlo es muy simple, ya que se le debe compartir a la herramienta el directorio a los archivos de código fuente que se desean analizar. Dicho comando tendría la siguiente forma:

    bandit -r directorio/a/codigo/fuente

Cuando se ejecuta el último comando en el directorio que contiene el código fuente del sensor. La aplicación permite especificar un "profile" y definir pruebas particulares. Si no se lo define, la herramienta por defecto ejecutará todos los tests. La salida que se obtiene luego de correr el comando en cuestión es la siguiente:

    (bandit-env) agustin@laptop:~$ bandit -r /home/agustin/open-traffic-detector/*.py
    [main]	INFO	profile include tests: None
    [main]	INFO	profile exclude tests: None
    [main]	INFO	cli include tests: None
    [main]	INFO	cli exclude tests: None
    [main]	INFO	running on Python 3.6.9
    Run started:2021-06-17 23:16:23.318913

    Test results:
        No issues identified.

    Code scanned:
        Total lines of code: 93
        Total lines skipped (#nosec): 0

    Run metrics:
        Total issues (by severity):
            Undefined: 0.0
            Low: 0.0
            Medium: 0.0
            High: 0.0
        Total issues (by confidence):
            Undefined: 0.0
            Low: 0.0
            Medium: 0.0
            High: 0.0
    Files skipped (0):

Como se puede apreciar, no se han encontrado vulnerabilidades en el código principal de la [aplicación](https://github.com/acurber91/open-traffic-detector). No obstante, como la misma se dividió en archivos para lograr un diseño modular, se analizaron independientemente todos los componentes de software y tampoco se encontraron vulnerabilidades.

---

![footer](doc/footer.png)