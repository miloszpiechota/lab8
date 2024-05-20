# Sprawozdanie LAB 8 Konfiguracja i wykorzystanie usługi Docker Scout. Analiza podatności obrazówDocker na zagrożenia bezpieczeństwa. Filtracja i interpretacja wyników dla poszczególnych składników obrazu.

# [Link do repozytorium DockerHub](https://hub.docker.com/repository/docker/miloszpiechota/lab8/general)


## 1. Budowanie obrazu Docker
```docker build -t miloszpiechota/lab8:test -f Dockerfile_multi .```

![image](https://github.com/miloszpiechota/lab8/assets/161620373/07b13b84-3b17-4c68-98f0-6600136126d0)


## 2. Polecenie Docker Scout służy do szybkiego podglądu informacji o obrazie Docker.
``` docker scout quickview miloszpiechota/lab8:test ```

![image](https://github.com/miloszpiechota/lab8/assets/161620373/b556d2be-ea17-449f-bb94-785351f4271f)


## 3. Polecenie Docker Scout służy do skanowania obrazu Docker w celu znalezienia potencjalnych podatności 
``` docker scout cves --format only-packages --only-vuln-packages --only-severity critical,medium miloszpiechota/lab8:test --platform linux/amd64```

![image](https://github.com/miloszpiechota/lab8/assets/161620373/df51375c-35e4-4c96-88e5-b5860dbb6b2e)


## 4. Zbudowanie obrazu po modyfikacji pliku package.json w którym użyto bezpiecznych wersji zidentyfikowanych pakietów.

![image](https://github.com/miloszpiechota/lab8/assets/161620373/75189c19-00a3-475e-9b5a-6012dc8e7e3d)

![image](https://github.com/miloszpiechota/lab8/assets/161620373/fd628409-6b04-4236-b543-cf983d1e08ae)


## 5. Modyfikując plik package.json udało się wyeliminować krytyczne i średnie luki w obrazie Dockera.

``` docker scout quickview miloszpiechota/lab8:test2```

![image](https://github.com/miloszpiechota/lab8/assets/161620373/7679e384-9b44-41c3-aec9-e4bbf02a6449)


![image](https://github.com/miloszpiechota/lab8/assets/161620373/1c86873f-b710-4fb0-a4b4-215cbcea2793)



