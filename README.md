# calculator1
just a simple try for calculator
import 'package:flutter/material.dart';

import 'package:flutter/material.dart';

void main() {
  runApp( MainApp());
}

class MainApp extends StatefulWidget {
   MainApp({super.key});

  @override
  State<MainApp> createState() => _MainAppState();
}

class _MainAppState extends State<MainApp> {
 double size=0;
String inputValue="";
String calculatedvalue="";
String operator="";
  @override
  Widget build(BuildContext context) {
     size=MediaQuery.of(context).size.width/12;
    return  MaterialApp(
      home: Scaffold(
        backgroundColor: Colors.black,
        body: Column(
          children: [
            Container(alignment: Alignment.bottomRight,
            child: Text(inputValue
            ,style:TextStyle(color: Colors.white,fontSize: 100),)
            ),
              Column(
                
                children: [
                  Row(
              
              children: [
                calcbutton("7",Colors.white38),
                calcbutton("8",Colors.white38),
                calcbutton("9",Colors.white38),
                calcbutton("/",Colors.orange),
              ],),
              
            
             Row(
              
              children: [
                calcbutton("4",Colors.white38),
                calcbutton("5",Colors.white38),
                calcbutton("6",Colors.white38),
                calcbutton("*",Colors.orange),
              ],),
              Row(
              
              children: [
                calcbutton("1",Colors.white38),
                calcbutton("2",Colors.white38),
                calcbutton("3",Colors.white38),
                calcbutton("-",Colors.orange),
              ],),
              Row(
              
              children: [
                calcbutton("0",Colors.white38),
                calcbutton(".",Colors.white38),
                calcbutton("=",Colors.white38),
                calcbutton("+",Colors.orange),
              ],),
                   
                ],
              ),   
              calcbutton("clear",Colors.black),
          ],
        ),
      ),
    );
  }
  Widget calcbutton(String text,Color backgroundColor){
    return InkWell(
      onTap:(){
        if(text=="clear"){
          setState(() {
            inputValue="";
            
          });

        } else if(text =="+" || text=="-" || text=="*" || text=="/"){
          setState(() {
            calculatedvalue=inputValue;
            inputValue="";

            operator=text;
          });
        }
        else if(text=="="){

          double calc=double.parse(calculatedvalue);
          double input=double.parse(inputValue);

          if(operator=="+"){
            inputValue=(calc+input).toString();
          }else  if(operator=="-"){
            inputValue=(calc-input).toString();
          }else  if(operator=="*"){
            inputValue=(calc*input).toString();
          }else  if(operator=="/"){
            inputValue=(calc/input).toString();
          }
          setState(() {
            inputValue=(double.parse(calculatedvalue)+double.parse(inputValue)).toString();
          });
        }
        
        
        else{
 setState(() {        
inputValue=inputValue+text;          
        });
    }
        },
       
      child: Container(
                    decoration: BoxDecoration(
                      color: Colors.white54,borderRadius: BorderRadius.circular(1000)
                    ),
                   
                    margin: EdgeInsets.all(10),
                  
                    height:size,
                    width: size,
                    alignment: Alignment.center,
                    child: Text("/",
                    style: TextStyle(color: Colors.white)),
                  ),
    );
                
}}
