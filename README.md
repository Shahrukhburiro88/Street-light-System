# Street-light-System
sbit LCD_RS at rd4_bit;
sbit LCD_en at rd5_bit;
sbit LCD_d7 at rd3_bit;
sbit LCD_d6 at rd2_bit;
sbit LCD_d5 at rd1_bit;
sbit LCD_d4 at rd0_bit;

// Pin direction
sbit LCD_RS_Direction at TRISd4_bit;
sbit LCD_EN_Direction at TRISd5_bit;
sbit LCD_D7_Direction at TRISd3_bit;
sbit LCD_D6_Direction at TRISd2_bit;
sbit LCD_D5_Direction at TRISd1_bit;
sbit LCD_D4_Direction at TRISd0_bit;


void main()
 {
 char i;
 char carcount[2];
 float car=0;
trisb.rb0 = 0;
trisb.rb1 = 1;
trisb.rb2 = 0;
trisb.rb3 = 1;
trisb.rb4= 0;
trisb.rb5=1;
          Lcd_Init();
   Lcd_Cmd(_LcD_CURSOR_OFF);



while (1)
{
     if (portb.rb1==1)
{
  car= car+1;
 floatTostr(car,carcount);
 Lcd_Cmd(_LCD_CLEAR);
 Lcd_Out(1, 4, "WElCOME");
   Lcd_Out(2, 2, "DRIVE SAFE");
    delay_ms(200);
     Lcd_Cmd(_LCD_CLEAR);

      Lcd_Out(1, 1, "Car Passed road");
      lcd_out(2,3,carcount);
      delay_ms(400);



}

//1
if (portb.rb1 == 1 && portb.rb3 == 0 && portb.rb5 ==0)
{
portb.rb0 = 1;
portb.rb2 = 0;
portb.rb4=0;

}
   //2
if (portb.rb1 == 0 && portb.rb3 == 1 && portb.rb5 ==0)
{
portb.rb0 = 0;
portb.rb2 = 1;
portb.rb4=0;
}
//3
if (portb.rb1 == 0 && portb.rb3 == 0 && portb.rb5 ==1)
{
portb.rb0 = 0;
portb.rb2 = 0;
portb.rb4=1;
}
//1,2
if (portb.rb1 == 1 && portb.rb3 == 1 && portb.rb5 ==0)
{
portb.rb0 = 1;
portb.rb2 = 1;
portb.rb4=0;
}
//1,3
 if (portb.rb1 == 1 && portb.rb3 == 0 && portb.rb5 ==1)
{
portb.rb0 = 1;
portb.rb2 = 0;
portb.rb4=1;
}
//2,3
if (portb.rb1 == 0 && portb.rb3 == 1 && portb.rb5 ==1)
{
portb.rb0 = 0;
portb.rb2 = 1;
portb.rb4=1;
}
//000
if (portb.rb1 == 0 && portb.rb3 == 0 && portb.rb5 ==0)
{
portb.rb0 = 0;
portb.rb2 = 0;
portb.rb4=0;
}

if (portb.rb1 == 1 && portb.rb3 == 1 && portb.rb5 ==1)
{
portb.rb0 = 1;
portb.rb2 = 1;
portb.rb4=1;
}

         if (porta.ra1==1)
         {
         Lcd_Cmd(_LCD_CLEAR);

              Lcd_Out(2, 2, "sukkur 90KM");
                 delay_ms(300);

    for(i=0; i<16;i++)
     {             // Move text to the left 7 times
      Lcd_Cmd(_LCD_SHIFT_right);
      delay_ms(50);
    }
    
     lcd_cmd(_lcd_clear);
    Lcd_Out(1, 1, " Karachi 112KM");
   Lcd_Out(2, 4, "MULTAN 87KM");
      delay_ms(300);
      }


   
}


}
