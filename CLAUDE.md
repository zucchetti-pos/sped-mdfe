# sped-mdfe — Constituição do Módulo

> SDK PHP para geração e comunicação de MDF-e (Manifesto Eletrônico de Documentos Fiscais) com SEFAZ. SDK externo — não modificar sem aprovação.

## Identidade
- Módulo: sped-mdfe — Emissão e comunicação de MDF-e com SEFAZ
- Fork: `nfephp-org/sped-mdfe`
- Parte do monorepo: zweb-projects

## Stack
- **Linguagem:** PHP ≥7.0
- **Dependências:** `nfephp-org/sped-common` · `justinrainbow/json-schema`
- **Extensões PHP obrigatórias:** zlib, dom, openssl, soap, json, simplexml, libxml
- **Testes:** PHPUnit ^7.5 + phpcs (PSR-2) + phpstan ^0.9
- **Gerenciador:** Composer
- **CI:** GitHub Actions

## Estrutura de pastas
```
sped-mdfe/
├── src/
│   ├── Common/         # Classes comuns (assinatura, validação)
│   ├── Exception/      # Exceções específicas
│   ├── Factories/      # Fábricas de documentos MDF-e
│   ├── Make.php        # Construção do XML MDF-e
│   ├── Tools.php       # Comunicação com SEFAZ (transmissão, consulta)
│   └── Complements.php # Complementos e eventos
├── schemes/            # Schemas XSD normativos do MDF-e
├── tests/              # Testes PHPUnit
└── phpunit.xml.dist
```

## Comandos do projeto
```bash
# Instalar dependências
composer install

# Executar testes
vendor/bin/phpunit -c phpunit.xml.dist

# Lint PSR-2
vendor/bin/phpcs --standard=psr2 src
vendor/bin/phpcbf --standard=psr2 src

# Análise estática
vendor/bin/phpstan analyse src --memory-limit=2048M
```

## Restrições
- **CRÍTICO:** Comunicação com SEFAZ não pode ser quebrada em nenhum deploy
- SDK externo (fork nfephp-org) — modificações exigem aprovação explícita
- PHP mínimo: 7.0
- Certificados digitais (A1/A3) e chaves privadas nunca em logs ou código
- Schemas XSD em `schemes/` são normativos — não alterar sem validação fiscal
- MDF-e é exigência legal para transporte de cargas — falhas geram autuação fiscal
