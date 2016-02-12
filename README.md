# AidlCommunication
Coomunication  between Service and Activity

with help of bind service we can comminicate with service.

1. Activty-----------> Service (Bind service ) we can call methods of service with help of Bind Objcet
2. Service - ----> Activty(get call back from service to Activity) we can achive this in Diff way
    a. with help of Inteface we can send callback from service to Activty \n
    b. LocalBrodacst Reciver\n
    c. with Handler \n
             Eg : Activty
                               public static class MessageHandler extends Handler {
                                    @Override
                                    public void handleMessage(Message message) {
                                        int state = message.arg1;
                                          switch (state) {
                                            case HIDE:
                                                progressBar.setVisibility(View.GONE);
                                                break;
                                            case SHOW:
                                                progressBar.setVisibility(View.VISIBLE);
                                                break;
                                        }
                                  }

                    when ever startservice at that time we have to pass handle Object .
                    Start your Service with this Handler object as an extra data as
                            public static Handler messageHandler = new MessageHandler();
                            Intent startService = new Intent(context, SERVICE.class)
                            startService.putExtra("MESSENGER", new Messenger(messageHandler));
                            context.startService(startService);
                            
                            
            Service  
            
            private Messenger messageHandler;
            Bundle extras = intent.getExtras();
            messageHandler = (Messenger) extras.get("MESSENGER");
           
            |
            |
            message.arg1 = Home.HIDE;
            messageHandler.send(message);
    
    d. with AIdL                      


