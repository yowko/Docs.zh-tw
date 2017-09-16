---
title: "-linkresource (C# 編譯器選項)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /linkresource
dev_langs:
- CSharp
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
caps.latest.revision: 17
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
ms.openlocfilehash: 022d6c1a53eab98fc033c902f903e7bc66e6da3f
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="linkresource-c-compiler-options"></a>/linkresource (C# 編譯器選項)
在輸出檔中建立 .NET Framework 資源連結。 資源檔不會新增至輸出檔。 這 一點與 [/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) 選項不同；後者會將資源檔內嵌在輸出檔中。  
  
## <a name="syntax"></a>語法  
  
```console  
/linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 您要從組件連結的目標 .NET Framework 資源檔。  
  
 `identifier` (選擇性)  
 資源的邏輯名稱；用來載入資源的名稱。 預設值是檔案的名稱。  
  
 `accessibility-modifier` (選擇性)  
 資源的存取範圍：公用或私用。 預設值是公用。  
  
## <a name="remarks"></a>備註  
 根據預設，使用 C# 編譯器建立連結資源時，這些資源在組件中為公用狀態。 若要將資源設為私用，可將 `private` 指定為存取範圍修飾詞。 您只能使用 `public` 或 `private` 修飾詞。  
  
 **/linkresource** 必須使用其中一個 [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) 選項 (**/target:module** 除外)。  
  
 例如，如果 `filename` 是由 [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) 或是在開發環境中所建立的 .NET Framework 資源檔，就可以使用 <xref:System.Resources> 命名空間中的成員進行存取。 如需詳細資訊，請參閱<xref:System.Resources.ResourceManager?displayProperty=fullName>。 至於其他所有資源，請使用 <xref:System.Reflection.Assembly> 類別中的 `GetManifestResource`* 方法在執行階段存取資源。  
  
 `filename` 中指定的檔案可以為任何格式。 例如，您可能需要產生組件的原生 DLL 部分，以便安裝到全域組件快取中，並從組件的 Managed 程式碼存取。 下方第二個範例顯示如何執行此操作。 您可以在組件連結器中執行相同的動作。 下方第三個範例顯示如何執行此操作。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](https://msdn.microsoft.com/library/c405shex) 和[使用組件和全域組件快取](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)。  
  
 **/linkres** 是 **/linkresource** 的簡短形式。  
  
 Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。  
  
## <a name="example"></a>範例  
 編譯 `in.cs` 並連結至 `rf.resource` 資源檔：  
  
```console  
csc /linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>範例  
 將 `A.cs` 編譯為 DLL，再連結至原生 DLL N.dll，並將輸出放入全域組件快取 (GAC) 中。 此範例的 A.dll 和 N.dll 都會位於 GAC 中。  
  
```console  
csc /linkresource:N.dll /t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a>範例  
 此範例會執行與上一個範例相同的動作，但改為使用組件連結器選項。  
  
```console  
csc /t:module A.cs  
al /out:A.dll A.netmodule /link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)   
 [Al.exe (組件連結器)](https://msdn.microsoft.com/library/c405shex)   
 [使用組件和全域組件快取](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)   
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)

