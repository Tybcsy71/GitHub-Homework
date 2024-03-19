# Docker image készítés GitHub Action használatával

Ez a repository Vagrant kódot tartalmaz, amelynek célja egy helyi GitLab CI/CD környezet beállítása, amely két virtuális gépből áll:
Ez a repository a Docker image elkészítéséhez szükséges fájlokat valamint egy GitHub Actiont tartalmaz.

## Tartalomjegyzék

- [Docker image készítés GitHub Action használatával](#docker-image-készítés-github-action-használatával)
  - [Tartalomjegyzék](#tartalomjegyzék)
  - [Repository tartalma](#repository-tartalma)
  - [Követelmények](#követelmények)
  - [Repository működése](#repository-működése)
    - [Docker image generálása](#docker-image-generálása)
    - [Docker image használata](#docker-image-használata)

## Repository tartalma

**Dockerfile**: Ezen file alapján készül egy docker image, amely tartalmaz egy NGINX-et, és egy saját kezdőoldalt.
**index.html**: Ez a saját kezdőoldal, amely bemásolásra kerül az image-be
**.github/workflows/main.yml**: Ez tartalmazza a workflow-t, amely legenerálja a Docker image-t, és feltölti a DockerHub-ra.

## Követelmények

A Docker image generálásához **tudnod kell commitolni ebbe a projektbe**.
A Docker image használatáhoza **rendelkezned kell a Docker image futtatásához szükséges Docker környezettel** a gépeden.

## Repository működése

### Docker image generálása

Commitolj ebbe a repositoryba.

Ennek hatására egy új image készül az alábbi DockerHub repository-ba latest taggel:
https://hub.docker.com/r/tibor71/homework

### Docker image használata

A docker image haszbálatához add ki a docker futtatására alkalmas gépen a `docker run -d -p <PORT>:80 tibor71/homework:latest`, cserélve a `<PORT>`-t arra a portra, amelyen el szeretnéd érni a gazdagépen a dockerben futó NGINX-et.

Ezt követően a `http://loclhost:<PORT>` linket megnyitva megjelenik a `DevOps homework by: Szente Tibor` felirat.

