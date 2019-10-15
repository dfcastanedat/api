## instrucciones para crear una querie o mutation

+ En typeDefs.js crear "type Nombre_del_objeto{atributos}" en el campo que corresponda, por ejemplo para chat en export const chatTypeDef=, con los atributos del objeto en la base de datos, por ejemplo:  
type Notification{  
    id: Int  
    message: String  
    sender_id: Int  
    chat_id: Int  
    user_id: Int  
}  
en id:Int! "!" indica que elcampo no puede ser nulo.  
tambien se puede crear uno para pasar como parametro:  
input UserInput {  
    id: Int  
    mail: String!  
    password: String!  
    username: String!  
    verification: Boolean  
    active: Boolean  
    password_confirmation: String!  
}  
+ En typeDefs.js crear (en const Querie o Mutation segun sea la peticion en el campo que corresponda, por ejemplo para queries de notification se pone en export const notificationQueries=), nombre_de_la_perticion(argumento1:tipo,argumento2:tipo):tipo_que_retorna ej: userById(id: Int!): User!


+ En resolvers.js crear en query o en mutation segun corresponda, nombre_de_la_peticion:(_,{parametros}) => generalRequest(url_de_la_ruta,tipo_de_peticion,parametros) ej   
allUsers: (_) =>  
		generalRequest(`${USERS_URL}/index`, 'GET')  

+ se pueden crear const con parte de la direccion, los puertos, etc en el archivo server.js hay que importarlos en resolvers.js para poder usarlos, las variables que estan ahi vienen de docker-compose.


## queries

# notifications

* query {  
  notificationById(user_id:14) {  
    id 	  
    user_id  
    message  
    chat_id  
  }  
}  

* mutation{  
  createNotification(notification:{   
    message: "wwewew"  
    sender_id: 12  
    chat_id: 12  
    users: [12 ,12,12,21]  
  }){  
    id  
  }  
}  

* mutation{  
	deleteNotification(user_id:12)  
}  

# users

* hay que cambiar users por User.all en el metodo index del controlador  
* query{  
  allUsers{  
    id  
    username  
    mail  
  }  
}  

* mutation {  
  createUser(user: {  
    username: "dxgcfh"  
    password: "123"  
    mail: "rstdtfygu"  
    verification:true  
    active: true  
    password_confirmation:"123"  
      
  }) {  
    username  
    id   
    mail  
  }  
}  

* mutation {  
  updateUser(user: {  
    id:1  
    username: "dgtffttftfttftft"  
    password: "123"  
    mail: "rstdtfygu"  
    verification:true  
    active: true  
    password_confirmation:"123"  
  }) {  
    username  
    id   
    mail  
  }  
}  

# states
* mutation{
  createState(State:{
    id_user: "dfc"
    about: "xdxd"
    image: "sajdnajdn"
  }){
    id
  }
}

* query{
  allStates{
    about
  }
}

* query{
  stateById(id: 1){
    about
  }
}
