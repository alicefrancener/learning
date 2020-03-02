# Coerção de tipos

- Inteiro para String

`function IntToStr(Value: Integer): string;`

- Float para String
  
`function FloatToStr(Value: Extended): string;`

- Float para String: especificando formato, precisão e dígitos 
  
`FloatToStrF(Value: Extended; Format: TFloatFormat; Precision, Digits: Integer): string`;

Formatos: ffCurrency, ffExponent, ffFixed, ffgeneral, ffNumber

---

- [Delphi Basics | SysUtils](http://www.delphibasics.co.uk/ByUnit.asp?Unit=SysUtils)  
- [Essential Pascal](http://www.marcocantu.com/epascal/English/ch03data.htm)