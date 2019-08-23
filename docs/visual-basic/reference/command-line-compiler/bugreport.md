---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 75c3e5842447a8f0812d5a90d7157f7a6a496936
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962437"
---
# <a name="-bugreport"></a>-bugreport
建立檔案, 您可以在提出 bug 報告時使用。  
  
## <a name="syntax"></a>語法  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`file`|必要項。 將包含 bug 報告的檔案名。 如果名稱包含空格, 請用引號 ("") 括住檔案名。|  
  
## <a name="remarks"></a>備註  
 下列資訊會新增至`file`:  
  
- 編譯中所有原始程式碼檔案的複本。  
  
- 編譯中使用的編譯器選項清單。  
  
- 您的編譯器、通用語言執行時間和作業系統的版本資訊。  
  
- 編譯器輸出 (如果有的話)。  
  
- 問題的描述, 會提示您。  
  
- 您認為問題的說明應如何修正, 而系統會提示您。  
  
 由於中`file`包含所有原始程式碼檔的複本, 因此您可能會想要在最短的可能程式中重現 (疑似) 程式碼缺失。  
  
> [!IMPORTANT]
> `-bugreport`選項會產生包含潛在敏感性資訊的檔案。 這包括目前時間、編譯器版本、.NET Framework 版本、作業系統版本、使用者名稱、編譯器執行時所使用的命令列引數、所有原始程式碼, 以及任何參考元件的二進位格式。 藉由在 web.config 檔案中指定命令列選項來進行 ASP.NET 應用程式的伺服器端編譯, 即可存取此選項。 若要避免這種情況, 請修改 Machine.config 檔案, 讓使用者不允許在伺服器上編譯。  
  
 如果搭配`-errorreport:prompt` `file` 、 `-errorreport:queue`或`-errorreport:send`使用此選項, 且您的應用程式發生編譯器內部錯誤, 則會將中的資訊傳送給 Microsoft Corporation。 這項資訊可協助 Microsoft 工程師找出錯誤的原因, 並可協助改善下一版的 Visual Basic。 根據預設, 不會將任何資訊傳送至 Microsoft。 不過, 當您使用`-errorreport:queue`來編譯應用程式時 (預設會啟用), 應用程式會收集其錯誤報表。 然後, 在電腦的系統管理員登入時, 錯誤報表系統會顯示一個快顯視窗, 可讓系統管理員將登入後發生的任何錯誤報表轉寄給 Microsoft。  
  
> [!NOTE]
> 此`/bugreport`選項無法從 Visual Studio 開發環境中使用; 只有當您從命令列編譯時, 才能使用此選項。  
  
## <a name="example"></a>範例  
 下列範例會編譯`T2.vb`並`Problem.txt`將所有 bug 報告資訊放在檔案中。  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [securityPolicy 的 trustLevel 元素 (ASP.NET 設定架構)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))
