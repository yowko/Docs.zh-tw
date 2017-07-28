---
title: "-addmodule (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /addmodule
dev_langs:
- CSharp
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
caps.latest.revision: 13
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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 614dbefbb472ef2cd03fcb1ba7a44f08c450bf4a
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="addmodule-c-compiler-options"></a>/addmodule (C# 編譯器選項)
此選項會將使用 target:module 參數所建立的模組新增至目前的編譯。  
  
## <a name="syntax"></a>語法  
  
```console  
/addmodule:file[;file2]  
```  
  
## <a name="arguments"></a>引數  
 `file`, `file2`  
 包含中繼資料的輸出檔案。 檔案不能包含組件資訊清單。 若要匯入多個檔案，請以逗號或分號分隔檔案名稱。  
  
## <a name="remarks"></a>備註  
 所有加上 **/addmodule** 的模組都必須和執行階段的輸出檔位於相同的目錄中。 也就是說，您可以在編譯時間指定任一目錄中的模組，但該模組於執行階段必須位在應用程式目錄中。 如果模組於執行階段不在應用程式目錄中，您就會有 <xref:System.TypeLoadException>。  
  
 `file` 不包含組件。 例如，如果輸出檔案是使用 [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) 所建立，則其中繼資料可使用 **/addmodule** 匯入。  
  
 如果輸出檔是以 **/target** 選項而不是以 **/target:module** 建立，則其中繼資料即無法以 **/addmodule** 匯入，但可以 [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) 匯入。  
  
 Visual Studio 不提供這個編譯器選項，專案無法參考模組。 此外，這個編譯器選項也不能以程式設計方式變更。  
  
## <a name="example"></a>範例  
 編譯來源檔案 `input.cs` 並從 `metad1.netmodule` 和 `metad2.netmodule` 新增中繼資料，以產生 `out.exe`：  
  
```console  
csc /addmodule:metad1.netmodule;metad2.netmodule /out:out.exe input.cs  
```  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [多檔案組件](../../../framework/app-domains/multifile-assemblies.md)   
 [操作說明：建置多檔案組件](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
