# Respostas referentes ao último commit, que força race condition a partir de variáveis auxiliares

1. 
- O saldo da vitrine nunca corresponde à quantidade real de pães disponíveis porque a variável global é sempre alterada pela última thread que termina de últilizá-la e essa sempre pega esse mesmo valor para trabalhar com ele novamente. Efetivamente é como se as duas threads trabalhassem com duas variáveis diferentes, pois elas obtém o valor da variável global e o utilizam logo após modificá-lo. Desse modo, a variável global fica com valores positivos que só aumentam na thread do padeiro e valores negativos que só diminuem na thread do cliente.
- O saldo ficou negativo sempre que era imprimido o valor dele pela thread do cliente, já que não havia uma correlação entre os valores trabalhados nela e os incrementos gerados pela thread do padeiro, mesmo ambas utilizando a variável global do saldo da vitrine.
- O saldo nunca mostrou o valor real de pães da vitrine, uma vez que as alterações do valor da variável global saldo vitrine em ambas as threads não afetavam umas às outras. Além disso, devido à essa falta de relação entre os valores da variável global nas threads, os valores das threads aumentavam na thread do padeiro e diminuiam na thread do cliente  sem parar, resultando tanto em muitos valores negativos como também valores que ultrapassavam o máximo estabelecido da vitrine (esperado, pois não foi implementada nenhuma condição para impedir isso).
- A thread do padeiro parece estar vencendo a corrida, porque ela é a primeira thread a executar um looping completo.

2. 
O problema acontece porque as duas threads pegam uma única versão da variável global e modificam ela paralalemente de forma que o valor da última que termina de utilizá-la sobrepõe o valor da primeira. Isso ocorre pois ambas trabalham com um valor desatualizado dessa variável global que não considera as modificações que a outra thread faz a ela. Dessa forma, como as duas threads competem por esse mesmo recurso, que é a variável global, e uma anula as modificações feitas pela outra, esse é um caso de Race Condition.

Resultado no monitor serial:
<img width="1600" height="1200" alt="WhatsApp Image 2026-11-11 at 13 15 48" src="https://github.com/user-attachments/assets/9f179b67-c0e4-4a96-a875-5082209a20db" />
