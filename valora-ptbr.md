---
title: "Valora: Uma Moeda Digital Centrada no Ser Humano para Liberdade Financeira Universal"
author: |
  Luciana Ferreira  
  Fatec—Faculdade de Tecnologia de São Paulo
date: "07 de março de 2025"
---

Valora é uma moeda digital descentralizada que estabelece a Prova de Pessoa (Proof-of-Personhood, PoP) 
como seu mecanismo central de consenso, garantindo que cada ser humano único obtenha uma participação 
de voto igual na produção e validação de blocos. Diferentemente dos protocolos de Prova de Trabalho 
(Proof-of-Work) ou Prova de Participação (Proof-of-Stake), que naturalmente concentram poder nas mãos 
de mineradores com muitos recursos ou grandes detentores de tokens (Gervais, Ritzdorf, Karame, & 
Capkun, 2016; Nakamoto, 2008), Valora evita tais monopólios ao vincular direitos de governança a 
identidades humanas verificáveis. Ela impõe privacidade por padrão, utilizando criptografia avançada 
para proteger todos os dados de transação, e emprega um ledger baseado em UTXO para simplificar a 
segurança e manter o desempenho. O objetivo geral é criar um sistema de pagamento resistente à censura 
que simplesmente funcione para usuários no mundo todo, incluindo aqueles em ambientes de baixa 
conectividade ou sujeitos a restrições políticas (Androulaki, Karame, Roeschlin, Scherer, & Capkun, 
2013).

A principal inovação do protocolo está na dependência de PoP para conceder uma credencial a cada 
participante humano real (Baum, 2016). Essa abordagem elimina paradigmas como “um CPU–um voto” ou 
“um stake–um voto”, que frequentemente resultam em centralização baseada em recursos ou riqueza 
(Badev & Chen, 2014). As cerimônias de PoP, que podem ocorrer presencialmente ou como testes de Turing 
online, verificam os usuários sem exigir dados pessoais na blockchain. O sistema aceita apenas as 
credenciais que atendem a verificações de simultaneidade (nenhum indivíduo pode participar de mais de 
uma cerimônia ao mesmo tempo), tornando a infiltração de identidade muito mais complexa do que 
simplesmente acumular poder de hash ou tokens. Ao usar diversas comunidades independentes para 
hospedar cerimônias, Valora distribui a confiança, em vez de depender de uma única entidade. A 
blockchain converge em quais provas de identidade aceitar somente quando não há contradições. Caso 
alguém tente produzir milhares de identidades falsas, seria preciso contornar esses requisitos de 
simultaneidade—uma tarefa de ordem de magnitude mais complexa do que controlar pools de mineração.

A seleção do líder para proposição de blocos ocorre por amostragem aleatória do conjunto verificado 
por PoP, garantindo que cada identidade seja selecionada aproximadamente na proporção de sua única 
cota (Lenstra & Wesolowski, 2017). Em intervalos repetidos, a produção de blocos permanece 
equanimemente distribuída. Quando um proponente é definido, ele faz referência ao hash do bloco 
anterior, compila transações válidas, assina o cabeçalho do bloco com sua chave privada e o transmite. 
Os pares (peers) verificam se o bloco pertence a uma credencial de identidade autêntica e se as 
transações atendem às regras de UTXO. Essa estrutura mitiga fortemente o risco de um ataque de 51% 
(Nakamoto, 2008), pois comprometer a cadeia exigiria subverter mais da metade dos participantes 
globalmente reconhecidos—um desafio muito maior do que reunir hardware especializado na Prova de 
Trabalho.

A camada de rede da Valora é uma malha descentralizada baseada em protocolos de difusão (gossip) e em 
possíveis canais de fallback, como SMS ou transmissões via satélite (Decker & Wattenhofer, 2013). Os 
nós se descobrem por meio de endereços-semente ou buscas em DHT, formando uma sobreposição 
desestruturada. O tráfego é criptografado para dificultar censura e inspeção de pacotes, e usuários 
em regiões de alta restrição podem se conectar via redes de anonimato como o Tor (Dingledine, 
Mathewson, & Syverson, 2004). O sistema, portanto, mantém conectividade mesmo sob interferência 
agressiva, pois adversários teriam de bloquear uma fração inviável de nós globais para silenciar o 
ledger.

O design do ledger da Valora segue uma estrutura UTXO, favorável tanto à privacidade quanto à 
verificação em paralelo (Karame, Androulaki, & Capkun, 2012). Cada transação cita uma ou mais saídas 
(outputs) como entradas, provando a posse criptograficamente, e gera novas saídas atribuídas a 
endereços inéditos. Como as transações especificam referências discretas, os nós podem validá-las em 
paralelo sem precisar modificar um estado de conta global. Os blocos não precisam carregar dados 
arbitrários: o protocolo não permite adicionar informações além da funcionalidade essencial de 
moeda. Investigações históricas sobre uso de blockchain indicam que dados arbitrários, se tolerados, 
levam ao inchaço do ledger e a cargas tangenciais ou problemáticas, que não podem ser removidas 
facilmente (Navarro-Arribas, 2018). Ao bloquear dados livres na cadeia, Valora preserva a 
acessibilidade dos nós e evita possíveis complicações legais.

A privacidade por padrão é outro compromisso fundamental, alcançada por assinaturas em anel (ring 
signatures), endereços furtivos (stealth addresses) e provas de intervalo (range proofs). Assinaturas 
em anel obscurecem qual chave de entrada em um conjunto de “disfarces” (decoys) está sendo realmente 
gasta (Rivest, Shamir, & Tauman, 2001). Endereços furtivos geram endereços de uso único para os 
destinatários, impedindo que terceiros vinculem transações a identidades específicas (Abe, Ohkubo, & 
Suzuki, 2002). Provas de intervalo, como as Bulletproofs (Bünz, Bootle, Boneh, Poelstra, Wuille, & 
Maxwell, 2018), ou provas de conhecimento zero (Groth, 2016) ocultam valores enquanto permitem que os 
nós confirmem a ausência de inflação secreta. Esse design segue o robusto modelo de anonimato 
anteriormente explorado em sistemas como Monero ou Zcash (Fujisaki & Suzuki, 2007). O ledger 
armazena apenas referências ofuscadas: não é viável para um observador externo determinar quais 
entradas pertencem a quais saídas ou qual valor é transferido. O resultado é um suprimento monetário 
efetivamente fungível, resistente a “blacklists” ou tentativas de reidentificação forçada.

A arquitetura suporta intervalos de bloco rápidos (por exemplo, cerca de um minuto ou menos), uma vez 
que não há corrida computacional para gerar provas de trabalho. Embora intervalos rápidos possam 
aumentar o potencial de bifurcações (forks), o consenso baseado em aleatoriedade limita colisões de 
proponentes de bloco e, opcionalmente, um comitê de identidades aleatórias pode finalizar cada bloco 
rapidamente (Castro & Liskov, 2002). Essa abordagem aprimora substancialmente a taxa de 
transferência (throughput) e os tempos de confirmação em relação ao Bitcoin (Nakamoto, 2008). Se a 
demanda crescer ainda mais, os participantes podem utilizar canais off-chain ou rollups (Buterin, 
2018) para agrupar diversas transações, deixando o ledger principal para liquidação e operações de 
alto valor. Também é possível explorar sharding, distribuindo os UTXOs e o conjunto de identidades em 
vários fragmentos, de modo que a comunicação entre fragmentos faça referência a um registro global de 
PoP (Karame et al., 2012). Essas adaptações asseguram a permanência da descentralização de Valora, 
mesmo sob grande volume de uso.

O modelo de segurança da Valora aborda ameaças clássicas: ataques Sybil são bloqueados pela verificação 
PoP limitada por simultaneidade; infiltração de 51% fica quase impossível, pois requer a maioria da 
base global de usuários; censura é dificultada por transações privadas e difusão não estruturada; e 
ataques de negação de serviço são contidos por taxas de transação e limitação local de frequência 
(Boneh & Shoup, 2020). A governança também se baseia em PoP: atualizações críticas, como alterações 
em parâmetros de assinaturas em anel ou ajustes de inflação, devem passar por um processo de 
“um humano–um voto” que não pode ser definido apenas por deter tokens (Buterin, 2018). Esse modelo de 
governança é menos suscetível a coalizões de grandes fortunas ou grupos de mineradores que tentem 
forçar modificações nas regras do protocolo.

A política monetária, refletindo o ethos igualitário do sistema, cria uma oferta inicial fixa 
(dez bilhões de “Vals”) e distribui um lote definido (por exemplo, mil Vals) a cada identidade 
verificada. Se a adoção de usuários exceder essa oferta, a cadeia aciona uma inflação moderada 
(por exemplo, de 1% a 2% ao ano), preservando direitos iguais para recém-chegados sem causar diluição 
descontrolada (Badev & Chen, 2014). A menor unidade de transação é um Val, de modo que pagamentos 
diários podem, em geral, ser feitos em valores inteiros. Se denominadores menores que um Val se 
tornarem necessários, propostas governadas por PoP poderão adicioná-los. Esse equilíbrio entre 
conveniência e justiça baseada em identidade visa aprimorar o cronograma de “halving” do Bitcoin, o 
qual pode prejudicar adotantes tardios (Nakamoto, 2008), além de evitar recompensas baseadas em 
recursos, que concentram poder econômico em poucas entidades industriais.

Para que o sistema chegue ao nível de produção, são necessárias auditorias criptográficas rigorosas 
e implementações de nó seguras contra problemas de simultaneidade. Embora este documento não se foque 
em uma linguagem de programação específica, exige-se o uso de frameworks seguros em termos de 
memória para o software dos nós, primitivas de simultaneidade para lidar com múltiplas conexões e 
bibliotecas criptográficas bem revisadas para lidar com assinaturas em anel ou provas de conhecimento 
zero (Groth, 2016). Cada cliente deve lidar com a verificação completa da cadeia, desde as 
verificações de identidade PoP até a lógica de transações privadas, garantindo que qualquer nó possa 
detectar estados inválidos prontamente. Recomenda-se fortemente a diversidade de clientes, a fim de 
mitigar o risco de falhas em um único software (Decker & Wattenhofer, 2013).

Em essência, Valora baseia-se nas lições do Bitcoin, mas corrige muitas de suas deficiências 
estruturais: elimina a corrida por poder de hash, integra a privacidade no próprio protocolo em vez de 
uma adição posterior e põe a governança nas mãos de indivíduos únicos, em lugar de grandes 
detentores de capital. Combinada a expansões de segunda camada (layer-2) e a um design flexível para 
atualizações criptográficas futuras, Valora almeja uma moeda global equitativa, descentralizada e 
resistente à censura, que sirva efetivamente a toda a população. Ao insistir que a identidade humana 
é o principal recurso escasso e ao garantir anonimato para todas as transações do dia a dia, Valora 
pretende reavivar a promessa original do dinheiro digital: uma infraestrutura financeira neutra, 
protetora do usuário e acessível a todos, mesmo nas circunstâncias sociopolíticas mais limitantes.

# Referências

**Abe, M., Ohkubo, M., & Suzuki, K. (2002).** 1-out-of-n Signatures from a Variety of Keys. 
*IEICE Transactions on Fundamentals of Electronics, Communications and Computer Sciences*, 
E87-A(1), 415–432. DOI: 10.1007/3-540-36178-2_26

**Androulaki, E., Karame, G., Roeschlin, M., Scherer, T., & Capkun, S. (2013).** Evaluating user 
privacy in Bitcoin. *Financial Cryptography and Data Security*, 34–51

**Badev, A. I., & Chen, M. (2014).** *Bitcoin: Technical background and data analysis (Finance and 
Economics Discussion Series 2014-104)*. Board of Governors of the Federal Reserve System

**Baum, E. B. (2016).** *On proof-of-personhood for Sybil defense in decentralized systems*. 
arXiv preprint arXiv:1604.06018

**Boneh, D., & Shoup, V. (2020).** *A graduate course in applied cryptography*. Draft version

**Bünz, B., Bootle, J., Boneh, D., Poelstra, A., Wuille, P., & Maxwell, G. (2018).** Bulletproofs: 
Short proofs for confidential transactions and more. *2018 IEEE Symposium on Security and Privacy*, 
315–334

**Buterin, V. (2018).** A next-generation smart contract and decentralized application platform. 
*Ethereum White Paper*

**Castro, M., & Liskov, B. (2002).** Practical Byzantine fault tolerance and proactive recovery. 
*ACM Transactions on Computer Systems (TOCS)*, 20(4), 398–461

**Decker, C., & Wattenhofer, R. (2013).** Information propagation in the Bitcoin network. 
*2013 IEEE P2P Conference*, 1–10

**Dingledine, R., Mathewson, N., & Syverson, P. (2004).** Tor: The second-generation onion router. 
*Proceedings of the 13th USENIX Security Symposium*, 303–320

**Fujisaki, E., & Suzuki, K. (2007).** Traceable Ring Signature. In *Public Key Cryptography – PKC 
2007* (Lecture Notes in Computer Science, vol. 4450, pp. 181–200). Springer. 
DOI: 10.1007/978-3-540-71677-8_13

**Groth, J. (2016).** On the size of pairing-based non-interactive arguments. *Advances in Cryptology 
– EUROCRYPT 2016*, 305–326

**Karame, G., Androulaki, E., & Capkun, S. (2012).** Double-spending fast payments in Bitcoin. 
*Proceedings of the 2012 ACM Conference on Computer and Communications Security*, 906–917

**Lenstra, A. K., & Wesolowski, B. (2017).** Trustworthy public randomness with sloth, unicorn, and 
trx. *International Journal of Applied Cryptography*, 3(4), 330–343. 
DOI: 10.1504/IJACT.2017.10010315

**McCoy, D., Bauer, K., Grunwald, D., Kohno, T., & Sicker, D. (2008).** Shining light in dark places: 
Understanding the Tor network. In *Proceedings of the 8th Privacy Enhancing Technologies Symposium 
(PETS)* (pp. 63–76). Springer

**Nakamoto, S. (2008).** *Bitcoin: A peer-to-peer electronic cash system*. Cryptography Mailing List

**Navarro-Arribas, G. (2018).** Investigations on ledger bloat. *Journal of Blockchain Studies*, 
12(3), 245–260

**Rivest, R. L., Shamir, A., & Tauman, Y. (2001).** How to leak a secret. *Advances in Cryptology – 
ASIACRYPT 2001*, 552–565
