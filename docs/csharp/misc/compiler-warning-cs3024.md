---
title: "編譯器警告 CS3024"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- CS3024
helpviewer_keywords:
- CS3024
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f175d102fa8a05b7f8c0a787564b933ff81cdf6c
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="compiler-warning-cs3024"></a>編譯器警告 CS3024
條件約束類型 'type' 不符合 CLS 標準。  
  
 由於使用不符合 CLS 標準的類型作為泛型類型條件約束，可能會使得以某些語言撰寫的程式碼無法使用您的泛型類別，因此編譯器會發出這個警告。  
  
### <a name="to-eliminate-this-warning"></a>移除這個警告  
  
1.  針對類型條件約束使用符合 CLS 標準的類型。  
  
## <a name="example"></a>範例  
 下列範例會在幾個位置產生 CS3024：  
  
```csharp  
// cs3024.cs  
// Compile with: /target:library  
 [assembly: System.CLSCompliant(true)]  
  
[type: System.CLSCompliant(false)]  
public class TestClass // CS3024  
{  
    public ushort us;  
}  
[type: System.CLSCompliant(false)]  
public interface ITest // CS3024  
{}  
public interface I<T> where T : TestClass  
{}  
public class TestClass_2<T> where T : ITest  
{}  
public class TestClass_3<T> : I<T> where T : TestClass  
{}  
public class TestClass_4<T> : TestClass_2<T> where T : ITest  
{}  
public class Test  
{  
    public static int Main()  
    {  
        return 0;  
    }  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [型別參數的條件約束](../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
