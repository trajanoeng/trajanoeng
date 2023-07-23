# Função para calcular a pegada de carbono empresarial
def calcular_pegada_carbono():
    # Fatores de emissão (gCO2e/kWh, gCO2e/l, gCO2e/km)
    fator_eletricidade = 0.5
    fator_combustivel = 2.3
    fator_viagens_nacionais = 0.15
    fator_viagens_internacionais = 0.3
    fator_onibus = 0.04
    fator_carro = 0.15
    fator_moto = 0.06
    fator_taxi = 0.15
    fator_outros = 0.1
    fator_ar_condicionado = 50
    fator_extintor_incendio = 30

    # Entradas do usuário
    numero_funcionarios = int(input("Quantos funcionários tem sua empresa? (Informe um número ou uma estimativa): "))
    consumo_eletricidade = float(input("Quanto você gastou com eletricidade no último mês em sua empresa (em kWh)? "))
    consumo_combustivel = float(input("Quanto você gastou com gerador de energia no último mês (em litros)? "))
    qtd_viagens_nacionais = int(input("Quantos voos nacionais ou dentro da América do Sul foram feitos pela empresa no último mês? "))
    qtd_viagens_internacionais = int(input("Quantos voos internacionais ou fora da América do Sul foram feitos pela empresa no último mês? "))
    qtd_funcionarios_onibus = int(input("Quantos funcionários utilizam ônibus para locomoção até o trabalho? "))
    qtd_funcionarios_carro = int(input("Quantos funcionários utilizam carros para locomoção até o trabalho? "))
    qtd_funcionarios_moto = int(input("Quantos funcionários utilizam motos para locomoção até o trabalho? "))
    qtd_funcionarios_taxi = int(input("Quantos funcionários utilizam táxis para locomoção até o trabalho? "))
    qtd_funcionarios_outros = int(input("Quantos funcionários utilizam outros meios de locomoção até o trabalho? "))
    recicla_lixo = input("Você recicla o lixo da sua empresa (copos descartáveis, papéis, etc)? (Sim ou Não): ").lower()
    recarga_ar_condicionado = input("Você realizou uma recarga de ar condicionado no último mês? (Sim ou Não): ").lower()
    recarga_extintor_incendio = input("Você realizou uma recarga de extintor de incêndio no último mês? (Sim ou Não): ").lower()

    # Cálculo das emissões
    emissao_eletricidade = consumo_eletricidade * fator_eletricidade
    emissao_combustivel = consumo_combustivel * fator_combustivel
    emissao_viagens_nacionais = qtd_viagens_nacionais * fator_viagens_nacionais
    emissao_viagens_internacionais = qtd_viagens_internacionais * fator_viagens_internacionais
    emissao_onibus = qtd_funcionarios_onibus * fator_onibus
    emissao_carro = qtd_funcionarios_carro * fator_carro
    emissao_moto = qtd_funcionarios_moto * fator_moto
    emissao_taxi = qtd_funcionarios_taxi * fator_taxi
    emissao_outros = qtd_funcionarios_outros * fator_outros
    emissao_ar_condicionado = fator_ar_condicionado if recarga_ar_condicionado == "sim" else 0
    emissao_extintor_incendio = fator_extintor_incendio if recarga_extintor_incendio == "sim" else 0

    # Cálculo da pegada de carbono total
    emissao_total = (
        emissao_eletricidade + emissao_combustivel + emissao_viagens_nacionais + emissao_viagens_internacionais +
        emissao_onibus + emissao_carro + emissao_moto + emissao_taxi + emissao_outros + emissao_ar_condicionado + emissao_extintor_incendio
    )

    # Cálculo da pegada de carbono por funcionário
    pegada_carbono_funcionario = emissao_total / numero_funcionarios

    # Cálculo do impacto mensal da empresa
    impacto_mensal_empresa = emissao_total

    # Cálculo do impacto anual da empresa
    impacto_anual_empresa = emissao_total * 12

    return pegada_carbono_funcionario, impacto_mensal_empresa, impacto_anual_empresa

# Chamada da função para calcular a pegada de carbono e obter os resultados
pegada_carbono, impacto_mensal, impacto_anual = calcular_pegada_carbono()

# Exibição dos resultados
print("A empresa está impactando o planeta com uma pegada de carbono de:", pegada_carbono, "gCO2e por funcionário.")
print("O impacto mensal da empresa é de:", impacto_mensal, "gCO2e.")
print("O impacto anual da empresa é de:", impacto_anual, "gCO2e.")
