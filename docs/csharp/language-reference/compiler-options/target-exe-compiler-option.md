---
title: "-target:exe (C# 編譯器選項)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /exe
dev_langs:
- CSharp
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
caps.latest.revision: 12
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
ms.openlocfilehash: bd035bffb697e895da8765f9e5d230fa84e98f04
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="targetexe-c-compiler-options"></a>/target:exe (C# 編譯器選項)
**/target:exe** 選項可讓編譯器建立可執行檔 (EXE)：主控台應用程式。  
  
## <a name="syntax"></a>語法  
  
```  
/target:exe  
```  
  
## <a name="remarks"></a>備註  
 **/target:exe** 選項預設為啟用。 將會建立副檔名為 .exe 的可執行檔。  
  
 使用 [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) 建立 Windows 程式可執行檔。  
  
 除非特別使用 [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) 選項指定輸出檔名稱，否則輸出檔名稱會採用包含 [Main](../../../csharp/programming-guide/main-and-command-args/index.md) 方法的輸入檔名稱。  
  
 指定於命令列時，下一個 **/out** 或 **/target:module** 選項之前的所有檔案都是用來建立 .exe 檔案。  
  
 編譯為 .exe 檔案的原始程式碼檔中只需要一個 **Main** 方法。 如果您的程式碼有多個具有 **Main** 方法的類別，則 [/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) 編譯器選項可讓您指定哪個類別包含 **Main** 方法。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性] 頁面。  
  
2.  按一下 [應用程式] 屬性頁。  
  
3.  修改 [輸出類型] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。  
  
## <a name="example"></a>範例  
 下列每個命令列都會建立 `in.exe` 來編譯 `in.cs`：  
  
```  
csc /target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a>另請參閱  
 [/target (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)

