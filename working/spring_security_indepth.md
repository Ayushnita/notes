# Spring Security   


Default pasword encder using in spring in DelegatingPasswordEncoder this is a map of all password encoder like:   



String idForEncode = "bcrypt";  
Map encoders = new HashMap<>();   
encoders.put(idForEncode, new BCryptPasswordEncoder());  
encoders.put("noop", NoOpPasswordEncoder.getInstance());  
encoders.put("pbkdf2", new Pbkdf2PasswordEncoder());  
encoders.put("scrypt", new SCryptPasswordEncoder());  
encoders.put("sha256", new StandardPasswordEncoder());  

PasswordEncoder passwordEncoder =  
    new DelegatingPasswordEncoder(idForEncode, encoders);  


So when you pass any password you pass it in {id}password format that {id} is map key from which you decide encoder.  
This behavior can be customized using DelegatingPasswordEncoder.setDefaultPasswordEncoderForMatches(PasswordEncoder).   

Ceating User   
User user = User.withDefaultPasswordEncoder()  
  .username("user")   
  .password("password")  
  .roles("user")  
  .build();  
System.out.println(user.getPassword());  
// {bcrypt}$2a$10$dXJ3SW6G7P50lGmMkkmwe.20cQQubK3.HZWzG3YB1tlRy.fqvM/BG    
