# CycleSoftware API documentation #

Repository of CycleSoftware API documentation 

## Usage ##

To generate docs run:

```bash
docker run --rm --name slate -v $pwd/docs:/srv/slate/build -v $pwd/source:/srv/slate/source slatedocs/slate; "docs.cyclesoftware.nl" > ./docs/CNAME
```
