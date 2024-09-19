# GitHub Actions Integracion Continua

* Actions es similar a Pipeline (DevObs)
* Archivos jenkins
* Workflow y Steps

## Conceptos
1. Workflow: archivo YAML que ejecuta acciones segun eventos.
2. Event: un disparador que inicia Workflow (trigger).
3. Job: trabajo dentro de un Workflow, se ejecutan en paralelo o en serie.
4. Step: accion individual dentro de un job.
5. Actions: bloque de codigo que realiza tareas dentro de un Step.
6. Runner: entorno de ejecucion de Jobs.

## YAML
* test.yaml or test.yml
* name: nombre del workflow
* on [?]: es un evento
* jobs: son el workflow
* primerjob y otro: nombre de jobs
* runs-on: especificar SO
* steps: ejecutar diferentes acciones
* run: permite ejecutar comandos
```
name: Prueba

on: [push]

jobs: 
  primerjob:
    runs-on: ubuntu-latest

    steps:
    - name: nombre
      run: echo "Esto es una Prueba"

  otro:
    runs-on: ubuntu-latest

    steps:
    - name: LS
      run: ls -al
```

