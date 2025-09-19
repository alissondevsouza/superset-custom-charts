# Superset Custom Charts

Um repositório de Helm Charts para Apache Superset customizado.

## Sobre

Este repositório contém charts Helm personalizados para deploy do Apache Superset em clusters Kubernetes.

## Charts Disponíveis

- **superset-custom**: Chart customizado do Apache Superset com configurações otimizadas

## Como Usar

### Adicionar o Repositório

```bash
helm repo add superset-custom https://SEU_USUARIO.github.io/superset-custom-charts/
helm repo update
```

### Instalar o Chart

```bash
# Instalação básica
helm install meu-superset superset-custom/superset

# Instalação com valores customizados
helm install meu-superset superset-custom/superset -f valores-customizados.yaml
```

### Buscar Charts Disponíveis

```bash
helm search repo superset-custom
```

## Configuração

### Valores Principais

```yaml
# Exemplo de configuração
image:
  repository: apache/superset
  tag: "latest"

service:
  type: ClusterIP
  port: 8088

ingress:
  enabled: true
  annotations: {}
  hosts:
    - host: superset.exemplo.com
      paths: ["/"]

postgresql:
  enabled: true

redis:
  enabled: true
```

## Desenvolvimento

### Pré-requisitos

- Helm 3.x
- Kubernetes 1.19+

### Como Contribuir

1. Fork este repositório
2. Crie uma branch para sua feature (`git checkout -b feature/nova-feature`)
3. Commit suas mudanças (`git commit -am 'Adiciona nova feature'`)
4. Push para a branch (`git push origin feature/nova-feature`)
5. Abra um Pull Request

### Atualizando Charts

Para adicionar uma nova versão do chart:

1. Atualize a versão em `Chart.yaml`
2. Empacote o chart: `helm package superset-custom/ -d charts/`
3. Atualize o index: `helm repo index charts/ --url https://SEU_USUARIO.github.io/superset-custom-charts/releases/download/`
4. Mova o index.yaml para a raiz: `mv charts/index.yaml ./`
5. Commit e push das mudanças

## Suporte

Para problemas ou dúvidas, abra uma [issue](https://github.com/SEU_USUARIO/superset-custom-charts/issues).

## Licença

Este projeto está licenciado sob a Licença Apache 2.0 - veja o arquivo [LICENSE](LICENSE) para detalhes.
