---
title: "-target:library (C# 編譯器選項)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /dll
dev_langs:
- CSharp
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
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
ms.openlocfilehash: c54599a3badf65fe6d53f74f71fde58772afa6c2
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="targetlibrary-c-compiler-options"></a>/target:library (C# 編譯器選項)
**/target:library** 選項可讓編譯器建立動態連結程式庫 (DLL)，而不是可執行檔 (EXE)。  
  
## <a name="syntax"></a>語法  
  
```  
/target:library  
```  
  
## <a name="remarks"></a>備註  
 將建立副檔名為 .dll 的 DLL。  
  
 除非特別使用 [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) 選項指定輸出檔名稱，否則輸出檔名稱會採用第一個輸入檔的名稱。  
  
 指定於命令列時，下一個 **/out** 或 **/target:module** 選項之前的所有檔案都是用來建立 .dll 檔案。  
  
 建置 .dll 檔案時，不需要 [Main](../../../csharp/programming-guide/main-and-command-args/index.md) 方法。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性] 頁面。  
  
2.  按一下 [應用程式] 屬性頁。  
  
3.  修改 [輸出類型] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。  
  
## <a name="example"></a>範例  
 建立 `in.dll` 以編譯 `in.cs`：  
  
```  
csc /target:library in.cs  
```  
  
## <a name="see-also"></a>另請參閱  
 [/target (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)

