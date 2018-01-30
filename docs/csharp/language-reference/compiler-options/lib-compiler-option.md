---
title: "-lib (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b60c6028d4b3f72acc31fe6028f7f956e1037eb0
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2018
---
# <a name="-lib-c-compiler-options"></a>-lib (C# 編譯器選項)
**-lib** 選項會使用 [-reference (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) 選項，來指定參考的組件位置。  
  
## <a name="syntax"></a>語法  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a>引數  
 `dir1`  
 如果編譯器在目前的工作目錄 (您叫用編譯器的起點目錄) 或通用語言執行平台的系統目錄中找不到參考的組件，會改為查詢的目錄。  
  
 `dir2`  
 用來尋找組件參考的一或多個其他目錄。 使用逗號分隔額外的目錄名稱；之間不含任何空白字元。  
  
## <a name="remarks"></a>備註  
 編譯器會以下列順序搜尋不完整的組件參考：  
  
1.  目前的工作目錄。 這是叫用編譯器的起點目錄。  
  
2.  通用語言執行平台系統目錄。  
  
3.  **-lib** 所指定的目錄。  
  
4.  LIB 環境變數所指定的目錄。  
  
 使用 **-reference** 來指定組件參考。  
  
 **-lib** 為加法；指定超過一次時，即會附加到任何先前的值。  
  
 若不想使用 **-lib**，替代方法是將任何必要的組件複製到工作目錄中；這樣一來，您就只需將組件名稱傳遞給 **-reference**。 接著，您就可以從工作目錄刪除組件。 由於資訊清單中未指定相依組件的路徑，因此應用程式可以在目標電腦上啟動，並在全域組件快取中尋找和使用組件。  
  
 即使編譯器可以參考組件，也不表示通用語言執行平台都能夠在執行階段尋找和載入組件。 如需執行階段如何搜尋參考組件的詳細資訊，請參閱[執行階段如何找出組件](../../../framework/deployment/how-the-runtime-locates-assemblies.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。  
  
2.  按一下 [參考路徑] 屬性頁。  
  
3.  修改清單方塊的內容。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>。  
  
## <a name="example"></a>範例  
 編譯 t2.cs 以建立 .exe 檔。 編譯器會在工作目錄和 C 磁碟機的根目錄中尋找組件參考。  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a>請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)  
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
