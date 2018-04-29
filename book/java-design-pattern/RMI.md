# RMI(Remote Method Invocation)
원격지에 있는 메소드를 호출하는것 

클라이언트(호출하는 쪽)에서 서버(호출받는 쪽)측을 호출할 수 있으려면 우선 어떤 메서드를 가지고 있는지 알아야 한다. 
제공할 메소드를 interface로 선언하여 클라이언트가 이를 인지하도록 해야 한다. 
이때 선언된 interface를 Remote interface라고 하고 호출할 메서드를 선언한다. 
그럼 서버측에서는 Remote interface에서 호출할 메서드의 구현체가 존재하여야 하며 호출시 Remote Object를 구동시켜서 마치 자신이 가진 메서드를
호출 한것 처럼 사용하면 된다. 