---
title: 編譯器警告 CS3024
ms.date: 07/20/2015
f1_keywords:
- CS3024
helpviewer_keywords:
- CS3024
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
ms.openlocfilehash: 7515fdd7bc8f57890e3f1aac6303ed4607cc2249
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688250"
---
# <a name="compiler-warning-cs3024"></a><span data-ttu-id="0bafa-102">編譯器警告 CS3024</span><span class="sxs-lookup"><span data-stu-id="0bafa-102">Compiler Warning CS3024</span></span>
<span data-ttu-id="0bafa-103">條件約束類型 'type' 不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="0bafa-103">Constraint type 'type' is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="0bafa-104">由於使用不符合 CLS 標準的類型作為泛型類型條件約束，可能會使得以某些語言撰寫的程式碼無法使用您的泛型類別，因此編譯器會發出這個警告。</span><span class="sxs-lookup"><span data-stu-id="0bafa-104">The compiler issues this warning because the use of a non-CLS-compliant type as a generic type constraint could make it impossible for code written in some languages to consume your generic class.</span></span>  
  
### <a name="to-eliminate-this-warning"></a><span data-ttu-id="0bafa-105">移除這個警告</span><span class="sxs-lookup"><span data-stu-id="0bafa-105">To eliminate this warning</span></span>  
  
1. <span data-ttu-id="0bafa-106">針對類型條件約束使用符合 CLS 標準的類型。</span><span class="sxs-lookup"><span data-stu-id="0bafa-106">Use a CLS-compliant type for the type constraint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bafa-107">範例</span><span class="sxs-lookup"><span data-stu-id="0bafa-107">Example</span></span>  
 <span data-ttu-id="0bafa-108">下列範例會在幾個位置產生 CS3024：</span><span class="sxs-lookup"><span data-stu-id="0bafa-108">The following example generates CS3024 in several locations:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0bafa-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bafa-109">See also</span></span>

- [<span data-ttu-id="0bafa-110">型別參數的條件約束</span><span class="sxs-lookup"><span data-stu-id="0bafa-110">Constraints on Type Parameters</span></span>](../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
