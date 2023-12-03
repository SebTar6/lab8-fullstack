## Konfiguracja do zadania z laboratorium 8 Programowanie Full-Stack w Chmurze Obliczeniowej

## Utwórz Namespace, Pod, Service, i NetworkPolicy

Aby utworzyć zasoby, należy użyć poniższego polecenia:

```bash
kubectl apply -f lab8.yaml
```

## Weryfikacja konfiguracji

# Weryfikacja działania podów, serwisów oraz polityki:

W namespace restricted:
```bash
kubectl get namespaces,pods,services,networkpolicies -n restricted
```
W namespace default (pody Sleepybox):
```bash
kubectl get pods
```

## Sprawdzenie dostępności usługi:

Z poda Sleepybox1:
```bash
kubectl exec -it Sleepybox1 -- sh
```
```bash
curl lab8server.restricted
```

# Pod Sleepybox1 będzie miał dostęp do serwera WWW (lab8server) na podstawie NetworkPolicy. 

Z poda Sleepybox2:
```bash
kubectl exec -it Sleepybox2 -- sh
```
```bash
curl lab8server.restricted
```

# W tym przypadku otrzymujemy błąd, ponieważ ruch ze Sleepybox2 nie jest uwzględniony w polityce Ingress.

## Wniosek

# Konfiguracja działa poprawnie, a NetworkPolicy ogranicza dostęp do usługi tylko dla wybranych Pod-ów.
