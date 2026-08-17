# De-para dos campos - Tradução PT

Este documento formaliza o mapeamento de entidades, colunas e valores categóricos do dataset original em inglês para os arquivos processados em português.

## 1. Mapeamento de Tabelas e Colunas

### Tabela: `patients` → `pacientes`
| Campo Original (`patients`) | Campo em Português (`pacientes`) |
| :--- | :--- |
| `patient_id` | `id_paciente` |
| *N/A (Novo Campo)* | `cpf` |
| `first_name` | `nome` |
| `last_name` | `sobrenome` |
| `gender` | `sexo` |
| `date_of_birth` | `data_nascimento` |
| `contact_number` | `telefone` |
| `address` | `endereco` |
| `registration_date` | `data_cadastro` |
| `insurance_provider` | `convenio` |
| `insurance_number` | `numero_convenio` |
| `email` | `email` |

### Tabela: `doctors` → `medicos`
| Campo Original (`doctors`) | Campo em Português (`medicos`) |
| :--- | :--- |
| `doctor_id` | `id_medico` |
| *N/A (Novo Campo)* | `cpf` |
| *N/A (Novo Campo)* | `crm` |
| `first_name` | `nome` |
| `last_name` | `sobrenome` |
| `specialization` | `especialidade` |
| `phone_number` | `telefone` |
| `years_experience` | `anos_experiencia` |
| `hospital_branch` | `unidade_hospitalar` |
| `email` | `email` |

### Tabela: `appointments` → `consultas`
| Campo Original (`appointments`) | Campo em Português (`consultas`) |
| :--- | :--- |
| `appointment_id` | `id_consulta` |
| `patient_id` | `id_paciente` |
| `doctor_id` | `id_medico` |
| `appointment_date` | `data_consulta` |
| `appointment_time` | `hora_consulta` |
| `reason_for_visit` | `motivo_consulta` |
| `status` | `status_consulta` |

### Tabela: `treatments` → `tratamentos`
| Campo Original (`treatments`) | Campo em Português (`tratamentos`) |
| :--- | :--- |
| `treatment_id` | `id_tratamento` |
| `appointment_id` | `id_consulta` |
| `treatment_type` | `tipo_tratamento` |
| `description` | `descricao` |
| `cost` | `custo` |
| `treatment_date` | `data_tratamento` |

### Tabela: `billing` → `faturamento`
| Campo Original (`billing`) | Campo em Português (`faturamento`) |
| :--- | :--- |
| `bill_id` | `id_fatura` |
| `patient_id` | `id_paciente` |
| `treatment_id` | `id_tratamento` |
| `bill_date` | `data_fatura` |
| `amount` | `valor` |
| `payment_method` | `forma_pagamento` |
| `payment_status` | `status_pagamento` |

---

## 2. Valores Categóricos Traduzidos

### `motivo_consulta` (`reason_for_visit`)
| Valor Original | Valor em Português |
| :--- | :--- |
| Therapy | Terapia |
| Consultation | Consulta de rotina |
| Emergency | Emergência |
| Checkup | Check-up |
| Follow-up | Retorno |

### `status_consulta` (`status`)
| Valor Original | Valor em Português |
| :--- | :--- |
| Scheduled | Agendada |
| No-show | Não compareceu |
| Cancelled | Cancelada |
| Completed | Concluída |

### `especialidade` (`specialization`)
| Valor Original | Valor em Português |
| :--- | :--- |
| Dermatology | Dermatologia |
| Pediatrics | Pediatria |
| Oncology | Oncologia |

### `forma_pagamento` (`payment_method`)
| Valor Original | Valor em Português |
| :--- | :--- |
| Insurance | Convênio |
| Credit Card | Cartão de Crédito |
| Cash | Dinheiro |

### `status_pagamento` (`payment_status`)
| Valor Original | Valor em Português |
| :--- | :--- |
| Pending | Pendente |
| Paid | Pago |
| Failed | Falhou |

### `tipo_tratamento` (`treatment_type`)
| Valor Original | Valor em Português |
| :--- | :--- |
| Chemotherapy | Quimioterapia |
| MRI | Ressonância Magnética |
| ECG | Eletrocardiograma |
| Physiotherapy | Fisioterapia |
| X-Ray | Raio-X |


### `descricao` (Tratamentos)
| Valor Original | Valor em Português |
| :--- | :--- |
| Basic screening | Triagem básica |
| Advanced protocol | Protocolo avançado |
| Standard procedure | Procedimento padrão |

### `unidade_hospitalar` (`hospital_branch`)
| Valor Original | Valor em Português |
| :--- | :--- |
| Westside Clinic | Clínica Zona Oeste |
| Eastside Clinic | Clínica Zona Leste |
| Central Hospital | Hospital Central |

---

## 3. Campos Novos Adicionados

Os seguintes campos foram incorporados na base em português e não possuem equivalência direta no dataset em inglês:

*   **`cpf`**: Adicionado às tabelas `pacientes` e `medicos` para identificação única
*   **`crm`**: Adicionado à tabela `medicos` para registro profissional

---

## 4. Dados Não Traduzidos e Justificativa

Para evitar distorção da informação e preservar os identificadores, os seguintes dados foram mantidos em seu formato/idioma original:

*   **Identificadores únicos (IDs)**: Mantiveram a mesma nomenclatura e prefixo (`P...`, `D...`, `A...`, `B...`, `T...`)
*   **Nomes próprios (`nome`, `sobrenome`)**: campos nome e sobrenome foram mantidos, pois correspondem a nomes próprios
*   **Endereços (`endereco`)**: Referem-se a localizações físicas próprias do dataset (ex.: "789 Pine Rd", "123 Elm St")
*   **Marcas / Operadoras de saúde (`convenio`)**: nomes das seguradoras (ex.: WellnessCorp, PulseSecure, HealthIndia)
*   **IDs de convênio (`numero_convenio`)**: identificadores como `INS...` foram preservados
*   **Endereços de e-mail (`email`)**: o domínio e a estrutura original do e-mail foram mantidos para consistência
*   **Valores de `sexo` (`F`, `M`)**: foram mantidos no formato original.