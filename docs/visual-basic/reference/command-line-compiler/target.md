---
title: /target (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8a8a9fcd6fa6dfaace01f8fbb7fa407145acc16f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="target-visual-basic"></a>/target (Visual Basic)
指定編譯器輸出的格式。  
  
## <a name="syntax"></a>語法  
  
```  
/target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## <a name="remarks"></a>備註  
 下表摘要說明的效果`/target`選項。  
  
|**選項**|**行為**|  
|----------------|------------------|  
|`/target:exe`|讓編譯器將建立可執行的主控台應用程式。<br /><br /> 這是預設選項時沒有`/target`指定選項。 可執行檔會建立副檔名為.exe。<br /><br /> 除非另有指定`/out`選項，輸出檔名稱會採用所包含的輸入檔的名稱`Sub Main`程序。<br /><br /> 只有一個`Sub Main`會編譯成.exe 檔的原始程式檔中所需的程序。 使用`/main`編譯器選項以指定哪一個類別包含`Sub Main`程序。|  
|`/target:library`|會導致編譯器建立的動態連結程式庫 (DLL)。<br /><br /> 動態連結程式庫檔案被建立.dll 副檔名。<br /><br /> 除非另有指定`/out`選項，輸出檔名稱會採用第一個輸入檔的名稱。<br /><br /> 當建置 DLL，`Sub Main`程序就不需要。|  
|`/target:module`|會導致編譯器產生的模組，可以加入組件。<br /><br /> .Netmodule 副檔名來建立輸出檔案。<br /><br /> .NET common language runtime 無法載入沒有組件的檔案。 不過，您可以將這類檔案合併的組件的組件資訊清單使用`/reference`。<br /><br /> 當其中一個模組中的程式碼參考另一個模組中的內部型別時，這兩個模組都必須加入至組件資訊清單使用`/reference`。<br /><br /> [/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)選項從模組匯入中繼資料。|  
|`/target:winexe`|可讓編譯器建立的可執行檔的 Windows 架構應用程式。<br /><br /> 可執行檔會建立副檔名為.exe。 Windows 應用程式是提供使用者介面，從[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]類別庫或搭配 Win32 Api。<br /><br /> 除非另有指定`/out`選項，輸出檔名稱會採用所包含的輸入檔的名稱`Sub Main`程序。<br /><br /> 只有一個`Sub Main`會編譯成.exe 檔的原始程式檔中所需的程序。 在您的程式碼已有多個類別`Sub Main`程序，使用`/main`編譯器選項以指定哪一個類別包含`Sub Main`程序|  
|`/target:appcontainerexe`|可讓編譯器建立的可執行 windows 應用程式必須在應用程式容器中執行。 這個設定設計用於[!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)]應用程式。<br /><br /> **Appcontainerexe**設定中的 [特性] 欄位設定一個位元[可攜式執行檔](http://go.microsoft.com/fwlink/p/?LinkId=236960)檔案。 此位元表示必須在應用程式容器中執行應用程式。 如果設定此位元時，發生錯誤`CreateProcess`方法嘗試啟動應用程式容器之外的應用程式。 此位元設定，除了**/target: appcontainerexe**相當於**/target: winexe**。<br /><br /> 可執行檔會建立副檔名為.exe。<br /><br /> 除非您另外指定使用`/out`選項，輸出檔名稱會採用所包含的輸入檔的名稱`Sub Main`程序。<br /><br /> 只有一個`Sub Main`會編譯成.exe 檔的原始程式檔中所需的程序。 如果您的程式碼會包含一個以上的類別具有`Sub Main`程序，使用`/main`編譯器選項以指定哪一個類別包含`Sub Main`程序|  
|`/target:winmdobj`|會導致編譯器建立中繼檔案，您可以將它轉換成 Windows 執行階段二進位檔 (.winmd) 檔案。 .Winmd 檔案可供 JavaScript 和 c + + 程式，除了 managed 的語言程式。<br /><br /> 副檔名為.winmdobj 建立中繼檔案。<br /><br /> 除非您另外指定使用`/out`選項，輸出檔名稱會採用第一個輸入檔的名稱。 A`Sub Main`程序不是必要的。<br /><br /> .Winmdobj 檔案設計來做為輸入<xref:Microsoft.Build.Tasks.WinMDExp>匯出工具來產生 Windows 中繼資料 (WinMD) 檔案。 WinMD 檔案副檔名.winmd，且包含的程式碼，原始的程式庫和 WinMD 定義該 JavaScript、 c + + 和 Windows 執行階段使用。|  
  
 除非您指定`/target:module`，`/target`導致[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]来加入至輸出檔的組件資訊清單。  
  
 會產生 Vbc.exe 的每個執行個體，最多一個輸出檔。 如果您指定編譯器選項，例如`/out`或`/target`一次以上，編譯器處理序放效果的最後一個。 在編譯中的所有檔案的相關資訊新增至資訊清單。 所有輸出檔案以外建立與`/target:module`包含資訊清單中的組件中繼資料。 使用[Ildasm.exe （IL 解譯器）](https://msdn.microsoft.com/library/f7dy01k1)檢視輸出檔中的中繼資料。  
  
 `/target` 的簡短形式為 `/t`。  
  
### <a name="to-set-target-in-the-visual-studio-ide"></a>在 Visual Studio IDE 中設定 /target  
  
1.  在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  按一下 [應用程式]  索引標籤。  
  
3.  修改中的值**應用程式類型**方塊。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`in.vb`、 建立`in.dll`:  
  
```  
vbc /target:library in.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [/out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [/moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)  
 [組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
