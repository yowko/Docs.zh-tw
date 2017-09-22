---
title: "-out (C# 編譯器選項)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /out
dev_langs:
- CSharp
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
caps.latest.revision: 15
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
ms.openlocfilehash: a6db728bc98f5223fc35268a1cce41021ff530cc
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="out-c-compiler-options"></a>/out (C# 編譯器選項)
**/out** 選項指定輸出檔案的名稱。  
  
## <a name="syntax"></a>語法  
  
```console  
/out:filename  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 編譯器所建立的輸出檔案名稱。  
  
## <a name="remarks"></a>備註  
 在命令列中，可以為您的編譯指定多個輸出檔案。 編譯器預期在 **/out** 選項之後找到一或多個原始程式碼檔。 之後，所有原始程式碼檔都會編譯至 **/out** 選項所指定的輸出檔案。  
  
 請指定您要建立的檔案的完整名稱和副檔名。  
  
 如果您未指定輸出檔案的名稱：  
  
-   .exe 的名稱將來自從包含 **Main** 方法的原始程式碼檔。  
  
-   .dll 或 .netmodule 的名稱將來自第一個原始程式碼檔。  
  
 用來編譯某個輸出檔案的原始程式碼檔，不能在同一個編譯中用於編譯另一個輸出檔。  
  
 在命令列編譯中產生多個輸出檔案時，請記住，只有其中一個輸出檔案可以是組件，而且只有 (使用 **/out** 隱含或明確) 指定的第一個輸出檔案可以是組件。  
  
 任何在編譯過程中產生的模組，都會變成與編譯中同時產生的任何組件建立關聯的檔案。 請使用 [ildasm.exe](https://msdn.microsoft.com/library/f7dy01k1) 來檢視組件資訊清單，以查看關聯的檔案。  
  
 必須有 /out 編譯器選項，才能讓 exe 成為 Friend 組件的目標。 如需詳細資訊，請參閱 [Friend 組件](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性] 頁面。  
  
2.  按一下 [應用程式] 屬性頁。  
  
3.  修改**組件名稱**屬性。  
  
     若要以程式設計方式設定這個編譯器選項：<xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> 是唯讀屬性，它是由專案類型 (exe、程式庫等等) 和組件名稱的組合所決定。 若要設定輸出檔案名稱，則必須修改一個或這兩個屬性。  
  
## <a name="example"></a>範例  
 編譯 `t.cs` 並建立 `t.exe` 輸出檔案，以及建置 `t2.cs` 並建立 `mymodule.netmodule` 模組輸出檔案：  
  
```console  
csc t.cs /out:mymodule.netmodule /target:module t2.cs  
```  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)   
 [Friend 組件](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)   
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)

