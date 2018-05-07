	const int blue = 1;   //These give the colors integer values
	const int green = 2;  //to make the code clearer to read.
	const int yellow = 3;
	const int red = 4;

	const int spkr = 3;   //the pin number that the speaker is connected to.

	const int s1 = 12;    //assign score digits to the 
	const int s2 = 13;    //appropriate pin numbers
	const int s3 = 14;
	const int s4 = 15;
	const int s5 = 16;
	const int s6 = 17;
	const int s7 = 18;

	int pattern[128];     //This is were the game sequence is stored
	int highscore = 0;    //Saves the player's high score
	int score = 0;        //Used to incriment the game, tracking how long the pattern is
	int color = 0;        //Used to pass the color of the button pressed.
	int speed = 50;       //Used in delay functions throughout the game to alter speed of gameplay.
	int song6[40];        //Used to store the tune to be played
	int rthm6[40];        //Used to store the rhythem of the tune to be played

	void allOff(){        //Turns off all LEDs
	  for(int i = 8; i < 19; i ++){
	    digitalWrite(i, LOW);
	  }
	}

	int setMusic(int song){// This function sets the values of the song
	                       // and rhythem arrays for each different tune to be played.
	const int c3 = 131;    // This replaced an earlier design that simply kept 
	const int cs3 = 139;   // a pair of global arrays for each song.
	const int d3 =  147;   // There are more notes defined than are actually used. 
	const int ds3 =  156;  // The values are all included so that new songs
	const int e3 =  165;   // can be created just using note names.
	const int f3 =  175;   // In addition to these notes, a 0 can be used for a rest.
	const int fs3 =  185;  //
	const int g3 =  196;   // The song6 array only holds the frequencies for the notes in order
	const int gs3 = 208;   // The rthm6 array holds the lengths of the notes at corresponding indicies
	const int a3 =  220;   // The return value of the function is the total number of notes and rests in the song
	const int as3 =  233;
	const int b3 =  247;
	const int c4 =  262;
	const int cs4 =  277;
	const int d4 =  294;
	const int ds4 = 311;
	const int e4 = 330;
	const int f4 = 349;
	const int fs4 = 370;
	const int g4 = 392;
	const int gs4 = 415;
	const int a4 = 440;
	const int as4 = 466;
	const int b4 = 494;
	const int c5 = 523;
	const int cs5 =554;
	const int d5 =  587;
	const int ds5 =  622;
	const int e5 =  660;
	const int f5 =  698;
	const int fs5 = 740;
	const int g5 = 784;
	const int gs5 =  831;
	const int a5 =  880;
	const int as5 =  932;
	const int b5 = 988;
	const int c6 =  1047;
	const int cs6 = 1109;
	const int d6 =  1175;
	const int ds6 = 1245;
	const int e6 =  1319;
	const int f6 =  1397;
	const int fs6 =  1480;
	const int g6 =  1568;
	const int gs6 =  1661;
	const int a6 =  1760;
	const int as6 =  1865;
	const int b6 =  1976;
	
	 if(song == 1){       //if the function is called with a 1, 
	                      //the song arrays are set to play the imperial march
	  song6[0] = d4;
	  song6[1] = d4;
	  song6[2] = d4;
	  song6[3] = as3;
	  song6[4] = f4;
	  song6[5] = d4;
	  song6[6] = as3;
	  song6[7] = f4;
	  song6[8] = d4;
	  song6[9] = a4;
	  song6[10] = a4;
	  song6[11] = a4;
	  song6[12] = as4;
	  song6[13] = f4;
	  song6[14] = d4;
	  song6[15] = as3;
	  song6[16] = f4;
	  song6[17] = d4;
	 
	  rthm6[0] = 4;
	  rthm6[1] = 4;
	  rthm6[2] = 4;
	  rthm6[3] = 3;
	  rthm6[4] = 1;
	  rthm6[5] = 4;
	  rthm6[6] = 3;
	  rthm6[7] = 1;
	  rthm6[8] = 8;
	  rthm6[9] = 4;
	  rthm6[10] = 4;
	  rthm6[11] = 4;
	  rthm6[12] = 3;
	  rthm6[13] = 1;
	  rthm6[14] = 4;
	  rthm6[15] = 3;
	  rthm6[16] = 1;
	  rthm6[17] = 8;
	  return 18;
	   
	 }else if(song == 2){  //if the function is called with a 2, 
	                       //the song arrays are set to play Eine Kleine Nachtmusik
	  song6[0] = c5;
	  song6[1] = g4;
	  song6[2] = c5;
	  song6[3] = g4;
	  song6[4] = c5;
	  song6[5] = g4;
	  song6[6] = c5;
	  song6[7] = e5;
	  song6[8] = g5;
	  song6[9] = f5;
	  song6[10] = d5;
	  song6[11] = f5;
	  song6[12] = d5;
	  song6[13] = f5;
	  song6[14] = d5;
 	  song6[15] = b4;
 	  song6[16] = d5;
 	  song6[17] = g4;
 	 
 	  rthm6[0] = 6;
 	  rthm6[1] = 2;
 	  rthm6[2] = 6;
 	  rthm6[3] = 2;
 	  rthm6[4] = 2;
 	  rthm6[5] = 2;
 	  rthm6[6] = 2;
 	  rthm6[7] = 2;
 	  rthm6[8] = 8;
 	  rthm6[9] = 6;
 	  rthm6[10] = 2;
 	  rthm6[11] = 6;
 	  rthm6[12] = 2;
 	  rthm6[13] = 2;
 	  rthm6[14] = 2;
 	  rthm6[15] = 2;
 	  rthm6[16] = 2;
 	  rthm6[17] = 8;
 	  return 18;
   
 	}else if(song == 3){  //if the function is called with a 3, 
 	                      //the song arrays are set to play Never Gonna Give You Up
 	  song6[0] = as3;
 	  song6[1] = c4;
 	  song6[2] = cs4;
 	  song6[3] = as3;
 	  song6[4] = f4;
 	  song6[5] = f4;
 	  song6[6] = ds4;
 	  song6[7] = gs3;
 	  song6[8] = as3;
 	  song6[9] = c4;
 	  song6[10] = gs3;
 	  song6[11] = ds4;
 	  song6[12] = ds4;
	  song6[13] = cs4;
	  song6[14] = c4;
	  song6[15] = as3;
	  song6[16] = as3;
	  song6[17] = c4;
	  song6[18] = cs4;
	  song6[19] = as3;
	  song6[20] = cs4;
	  song6[21] = ds4;
	  song6[22] = c4;
	  song6[23] = as3;
	  song6[24] = gs3;
	  song6[25] = f3;
	  song6[26] = ds4;
	  song6[27] = cs4;
	 
	  rthm6[0] = 1;
	  rthm6[1] = 1;
	  rthm6[2] = 1;
	  rthm6[3] = 1;
	  rthm6[4] = 3;
	  rthm6[5] = 3;
	  rthm6[6] = 6;
	  rthm6[7] = 1;
	  rthm6[8] = 1;
	  rthm6[9] = 1;
	  rthm6[10] = 1;
	  rthm6[11] = 3;
	  rthm6[12] = 3;
	  rthm6[13] = 3;
	  rthm6[14] = 1;
	  rthm6[15] = 3;
	  rthm6[16] = 1;
	  rthm6[17] = 1;
	  rthm6[18] = 1;
	  rthm6[19] = 1;
	  rthm6[20] = 5;
	  rthm6[21] = 2;
	  rthm6[22] = 2;
	  rthm6[23] = 2;
	  rthm6[24] = 3;
	  rthm6[25] = 1;
	  rthm6[26] = 4;
	  rthm6[27] = 4;
	  return 28;
	   
	}else if(song == 4){ //if the function is called with a 4, 
	                     //the song arrays are set to play the Indiana Jones Theme
	  song6[0] = e4;
	  song6[1] = f4;
	  song6[2] = g4;
	  song6[3] = c5;
	  song6[4] = d4;
	  song6[5] = e4;
	  song6[6] = f4;
	  song6[7] = g4;
	  song6[8] = a4;
	  song6[9] = b4;
 	  song6[10] = f5;
	  song6[11] = a4;
	  song6[12] = b4;
	  song6[13] = c5;
	  song6[14] = d5;
	  song6[15] = e5;
 
	  rthm6[0] = 3;
	  rthm6[1] = 1;
	  rthm6[2] = 2;
	  rthm6[3] = 8;
	  rthm6[4] = 3;
	  rthm6[5] = 1;
	  rthm6[6] = 8;
	  rthm6[7] = 3;
	  rthm6[8] = 1;
	  rthm6[9] = 2;
	  rthm6[10] = 8;
	  rthm6[11] = 3;
	  rthm6[12] = 1;
	  rthm6[13] = 4;
	  rthm6[14] = 4;
	  rthm6[15] = 4;
	  return 16;
	   
	 }else if(song == 5){ //if the function is called with a 5, 
	                      //the song arrays are set to play the Pirates of the Caribbean Theme
	  song6[0] = g3;
	  song6[1] = 0;
	  song6[2] = g3;
	  song6[3] = 0;
	  song6[4] = as3;
	  song6[5] = c4;
	  song6[6] = g3;
	  song6[7] = 0;
	  song6[8] = g3;
	  song6[9] = 0;
	  song6[10] = f3;
	  song6[11] = fs3;
	  song6[12] = g3;
	  song6[13] = 0;
	  song6[14] = g3;
	  song6[15] = 0;
	  song6[16] = as3;
	  song6[17] = c4;
	  song6[18] = g3;	
	  song6[19] = 0;
	  song6[20] = g3;
	  song6[21] = 0;
	  song6[22] = f3;	
	  song6[23] = fs3;
	  song6[24] = g3;
	   
	  rthm6[0] = 2;
	  rthm6[1] = 1;
	  rthm6[2] = 2;
	  rthm6[3] = 1;	
	  rthm6[4] = 2;
	  rthm6[5] = 2;
	  rthm6[6] = 2;
	  rthm6[7] = 1;
	  rthm6[8] = 2;
	  rthm6[9] = 1;
	  rthm6[10] = 2;
	  rthm6[11] = 2;
	  rthm6[12] = 2;
	  rthm6[13] = 1;
	  rthm6[14] = 2;
	  rthm6[15] = 1;
	  rthm6[16] = 2;
	  rthm6[17] = 2;
	  rthm6[18] = 2;
	  rthm6[19] = 1;
	  rthm6[20] = 2;
	  rthm6[21] = 1;
	  rthm6[22] = 2;
	  rthm6[23] = 2;
	  rthm6[24] = 3;  
	  return 25;
   
	 }else if(song == 6){ //if the function is called with a 6, 
	                      //the song arrays are set to play the Mission Impossible Theme
	  song6[0] = a4;
	  song6[1] = c5;
	  song6[2] = d5;
	  song6[3] = d5;
	  song6[4] = 0;  
	  song6[5] = d5;
	  song6[6] = e5;
	  song6[7] = f5;
	  song6[8] = f5;
	  song6[9] = 0;    
	  song6[10] = f5;
	  song6[11] = g5;
	  song6[12] = e5;
	  song6[13] = e5;
	  song6[14] = 0;   
	  song6[15] = d5;
	  song6[16] = c5;
	  song6[17] = c5;
	  song6[18] = d5;
	  song6[19] = 0;    
	  song6[20] = a4;  
	  song6[21] = c5;
	  song6[22] = d5;
	  song6[23] = d5;
	  song6[24] = 0;    
	  song6[25] = d5;
	  song6[26] = e5;
	  song6[27] = f5;
	  song6[28] = f5;
	  song6[29] = 0;    
	  song6[30] = f5;
	  song6[31] = g5;
	  song6[32] = e5;
	  song6[33] = e5;
	  song6[34] = 0;    
	  song6[35] = d5;
	  song6[36] = c5;
	  song6[37] = d5;
	  song6[38] = 0;  
	  
	  rthm6[0] = 2;
	  rthm6[1] = 2;
	  rthm6[2] = 4;
	  rthm6[3] = 3;
	  rthm6[4] = 1;  
	  rthm6[5] = 2;
	  rthm6[6] = 2;
	  rthm6[7] = 4;
	  rthm6[8] = 3;
	  rthm6[9] = 1;  
	  rthm6[10] = 2;
	  rthm6[11] = 2;
	  rthm6[12] = 4;
	  rthm6[13] = 3;
	  rthm6[14] = 1;  
	  rthm6[15] = 2;
	  rthm6[16] = 2;
	  rthm6[17] = 2;
	  rthm6[18] = 6;
	  rthm6[19] = 2;  
	  rthm6[20] = 2;
	  rthm6[21] = 2;
	  rthm6[22] = 4;
	  rthm6[23] = 3;
	  rthm6[24] = 1;  
	  rthm6[25] = 2;
	  rthm6[26] = 2;
	  rthm6[27] = 4;
	  rthm6[28] = 3;
	  rthm6[29] = 1;  
	  rthm6[30] = 2;
	  rthm6[31] = 2; 
	  rthm6[32] = 4;
	  rthm6[33] = 3;
	  rthm6[34] = 1;  
	  rthm6[35] = 2;
	  rthm6[36] = 2;
	  rthm6[37] = 7;
	  rthm6[38] = 1;  
	  return 39;
	   
	 }
	 return 0;
	}
	
	void showHighscore(){     //This function displays the current high score
	  digitalWrite(s7, LOW);  // first it turns all lights off
	  digitalWrite(s6, LOW);
	  digitalWrite(s5, LOW);
	  digitalWrite(s4, LOW);
	  digitalWrite(s3, LOW);
	  digitalWrite(s2, LOW);
	  digitalWrite(s1, LOW);
	  int temp = highscore;  //a temporary varialbe is used to preserve the high score value
	  if(temp > 127){        //The max displayable score is 127, this prevents errors in the highly
	    temp = 127;          //unlikely scenario that the player excedes this
	   }
	  if(temp > 63){         //Starting with the highest valued light (64)
	    digitalWrite(s7, HIGH);
	    temp -= 64;          //if the highscore is above that value, turn the light on and  
	  }                      //subtract it from the temp value
	  if(temp > 31){         //repeat this process using place values of a binary number
	    digitalWrite(s6, HIGH);
	    temp -= 32;          //until the whole high score has been displayed.
	  }
	  if(temp > 15){
	    digitalWrite(s5, HIGH);
	    temp -= 16;
	  }
	  if(temp > 7){
	    digitalWrite(s4, HIGH);
	    temp -= 8;
	  }
	  if(temp > 3){
	    digitalWrite(s3, HIGH);
	    temp -= 4;
	  }
	  if(temp > 1){
	    digitalWrite(s2, HIGH);
	    temp -= 2;
	  }
	  if(temp > 0){
	    digitalWrite(s1, HIGH);
	    temp -= 1;
	  } 
	}
	
	void playTune(int tune){  //This is the function called to play each song
	    allOff();             //Turn all the lights off in preperation for the light show
	    int length = setMusic(tune); //defines the length of the song and sets the song arrays
	    int tempo = 0;        //used to determine the speed of the song
	    int light = 8;        //used to turn lights on and off in sequence with the music
	    int tmp = 0;          //used for comparisons to determine which way to move the light.
	    
	    if(tune == 1){        //These lines set the appropriate tempo for each song.
	      tempo = 100;
	    }else if(tune == 2){
	      tempo = 60;
	    }else if(tune == 3){
	      tempo = 80;
	    }else if(tune == 4){
	      tempo = 80;
	    }else if(tune == 5){
	      tempo = 60;
	    }else if(tune == 6){
	      tempo = 40;
	    }
	    
	    digitalWrite(light, HIGH);       //This is the start of the lightshow, turning the first light on
	    for(int i = 0; i < length; i++){ //it uses a loop to read each note of the song
	    play(song6[i], rthm6[i], tempo); //first play the note
	        digitalWrite(light, LOW);    //turn the previous light off
	        if(song6[i] >= tmp){         //if the current note is the same or higher than the previous note,
	            if(light == 18){         //move the light one way
	                light = 8;
	            }else{
	                light += 1;
	            }
	        }else{                       //if the note is lower than the previous note,
	            if(light == 8){          //move the light the other way.
	                light = 18;
	            }else{
	                light -= 1;
	            }
	        }
	        digitalWrite(light, HIGH);   //turn on the next light
	        tmp = song6[i];              //remember the previous note for next time
	  }
	  allOff();                          //turn all the lights off at the end of the song
	}
	
	void play(int note, int len, int tpo){//this function sends the command to the speaker to play each note
	  if(note == 0){                      //This plays a rest
	    delay(2*tpo*len);
	  }else{
	    tone(spkr, note);                 //this turns the sound on and off
	      delay(tpo*len);
	    noTone(spkr);
	      delay(tpo*len);                 //then allows some space to separate notes
	  }
	}
	
	void lose(){                          //this defines what happens if the player makes a mistake
	  int light = 9;                      //start the lightshow
	  digitalWrite(light, HIGH);
	  for(int i = 1175; i >= 294; i --){  //defines a decreasing pitch landing on the first note 
	                                      //of the imperial march
	    tone(spkr, i);
	    
	    if(i % 12 == 0){                  //%12 is used to slow the progression of lights to a 
	      digitalWrite(light, LOW);       //resonable pace. The lights progress in a circle
	      if(light == 8){
	          light = 18;
	      }else{
	          light = light - 1;
	      }
	      digitalWrite(light, HIGH);
	    }  
	    delay(4);
	    noTone(spkr);
	  }
	  noTone(spkr);
	  digitalWrite(light, LOW);
	  playTune(1);                         //play the imperial march
	      showHighscore();                 //display the old high score
	      delay(1000);                     //suspense
	  if(score > highscore){               //if a new highscore has been achieved
	      playTune(2);                     //play Mozart
      highscore = score;               //save the new highscore
	  }   
	      showHighscore();                 //show the new highscore
	      score = -1;                      //-1 is used because the incrimentation of the score
	}                                      //comes after the lose function in the main loop and will 
	                                       //therefore set the score to 0 for the restart.
	void start(){
	  int light = 8;                       //startup sequence
	  for(int i = 0; i <= 523; i++){       //defines an increasing pitch landing on a c
	    
	    tone(spkr, i);
	    
	    if(i % 12 == 0){                   //mod 12 is used to slow down the circular motion of the lights.
	      digitalWrite(light, LOW);
	      if(light == 18){
	          light = 8;
	      }else{
	          light += 1;
	      }
	      digitalWrite(light, HIGH);
	    }
	    
	    if(i == 523){                      //holds the last note
	        delay(500);
	    }else{
	      delay(5);
	    }
	  }
	  noTone(spkr);                        //turn off the light and sound
	  digitalWrite(light, LOW);
	 
	}
	
	void check(int condition){             //this function waits for a button to be pressed
	  int light = 8;
	  while(color == 0){                   //this loop will continue until a button is pressed
	    if(condition > 0){                 //this condition changes the function for the start 
	      condition++;                     //of the game. It adds flashing the colored lights
	      digitalWrite(light, HIGH);       //in sequence to indicate the player must pick one.
	    }
	    int push = 0;                      //this loop checks each of the buttons
	    for(int i = 4; i < 8 && color == 0; i++){
	        push = digitalRead(i);
	        if(push){                      //if a button has been pressed
	            color = i - 3;             //the color of the button is saved
	        }
	     }
	
	     if(condition == 10000){           //this statement slows down the light sequence,
	        digitalWrite(light, LOW);      //changing every 10000 times the loop runs.
	        if(light == 11){
	            light = 8;
	        }else{
	            light += 1;
	        }
	        condition = 1;
	     }
	  }
	}
	
	void blink(int a){              //This blinks the indicated light and plays its corresponding tone
	  digitalWrite(a + 7, HIGH);
	    if(a == blue){
	      tone(spkr, 262); 
	    }else if(a == green){
	      tone(spkr, 294);
	    }else if(a == yellow){
	      tone(spkr, 392);
	    }else{
	      tone(spkr, 523);
	    }
	    delay(speed * 5);           //The speed variable in incorperated to change the pace of the game
	    noTone(spkr);
	    delay(speed * 5);
	    digitalWrite(a + 7, LOW);
	    
	    delay(speed * 10);
	}
	  
	void setup(){                  //set the pins to appropriate input our output state
	  pinMode(3, OUTPUT);
	  pinMode(4, INPUT);
	  pinMode(5, INPUT);
	  pinMode(6, INPUT);
	  pinMode(7, INPUT);
	  pinMode(8, OUTPUT);
	  pinMode(9, OUTPUT);
	  pinMode(10, OUTPUT);
	  pinMode(11, OUTPUT);
	  pinMode(12, OUTPUT);
	  pinMode(13, OUTPUT);
	  pinMode(14, OUTPUT);
	  pinMode(15, OUTPUT);
	  pinMode(16, OUTPUT);
	  pinMode(17, OUTPUT);
	  pinMode(18, OUTPUT);
	  
	  start();                     //run the startup sequence
	      
	  randomSeed(analogRead(5));   //seed the random number generator with "random" background  
	}                              //noise from the unconnected analog pin
	
	void loop(){                     //This is the main loop of the game
	  if(score == 0){                //if it is the beginning of the game
	    
	  check(1);                      //flash the lights and wait for the player to pick a speed
	    if(color == blue){           //set the speed and play the corresponding tune
	      speed = 50;
	      delay(1000);
	    playTune(3); 
	    }
	    if(color == green){
	      speed = 35;
	      delay(1000);
	    playTune(4);       
	    }
	    if(color == yellow){
	      speed = 20;
	      delay(1000);
	        playTune(6);          
	    }
	    if(color == red){
	      speed = 12;
	      delay(1000);
	      playTune(5); 
	    }
	    color = 0;
	  delay(1000);
	  }
	    showHighscore();                //start by displaying the current high score
	    pattern[score] = random(1, 5);  //set the next light in the sequence
	    
	  for(int j = 0; j <= score; j++){  //blink the sequence
	      blink(pattern[j]);
	    }
	  for(int j = 0; j <= score; j++){  //let the player repeat the sequence
	    check(0);
	    if(color == pattern[j]){        //if the input matches the sequence
	      blink(color);                 //blink the light and continue
	      color = 0;
	    }else{                          //if the player gets it wrong
	      color = 0;
	      lose();                       //they lose
	    }
	  }
	  score++;        //if the player makes it all the way through the sequence with no mistakes
	  delay(1000);    //increase the score by one and start over
	}
