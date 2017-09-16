---
title: "-moduleassemblyname (C# 編譯器選項)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /moduleassemblyname
dev_langs:
- CSharp
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2522609aa41ad944b37a8882c1cc56cd5967b330
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="moduleassemblyname-c-compiler-option"></a>/moduleassemblyname (C# 編譯器選項)
指定 .netmodule 可以存取其非公用類型的組件。  
  
## <a name="syntax"></a>語法  
  
```console  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>引數  
 `assembly_name`  
 .netmodule 可以存取其非公用類型之組件的名稱。  
  
## <a name="remarks"></a>備註  
 **/moduleassemblyname** 應該在建置 .netmodule 時，以及符合下列條件時使用：  
  
-   .netmodule 需要存取現有組件中的非公用類型。  
  
-   您知道將在其中建置 .netmodule 之組件的名稱。  
  
-   現存組件已對將在其中建置 .netmodule 的組件授與 friend 組件的存取權。  
  
 如需建置 .netmodule 的詳細資訊，請參閱 [/target:module (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)。  
  
 如需 Friend 組件的詳細資訊，請參閱 [Friend 組件](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)。  
  
 這個選項不適用於開發環境；只有在從命令列編譯時才可用。  
  
 Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。  
  
## <a name="example"></a>範例  
 此範例會建置具有私用類型的組件，並提供 Friend 組件存取權給稱為 csman_an_assembly 的組件。  
  
```csharp  
// moduleassemblyname_1.cs  
// compile with: /target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class   
{  
    public void Test()   
    {   
        Console.WriteLine("An_Internal_Class.Test called");   
    }  
}  
```  
  
## <a name="example"></a>範例  
 此範例將建置的 .netmodule 會存取 moduleassemblyname_1.dll 組件中的非公用類型。 藉由得知此 .netmodule 將建置在稱為 csman_an_assembly 的組件中，因此可以指定 **/moduleassemblyname**，讓 .netmodule 在授與 Friend 組件存取權給 csman_an_assembly 的組件中存取非公用類型。  
  
```csharp  
// moduleassemblyname_2.cs  
// compile with: /moduleassemblyname:csman_an_assembly /target:module /reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## <a name="example"></a>範例  
 此程式碼範例將會建置 csman_an_assembly 組件，並參考之前建置的組件及 .netmodule。  
  
```csharp  
// csman_an_assembly.cs  
// compile with: /addmodule:moduleassemblyname_2.netmodule /reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
 **已呼叫 An_Internal_Class.Test**   
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)   
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)

