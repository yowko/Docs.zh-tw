---
title: "Clrver.exe (CLR 版本工具)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f8bef6f85f9e4b7d35e60c613a12ad87a26b70ab
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="clrverexe-clr-version-tool"></a>Clrver.exe (CLR 版本工具)
CLR 版本工具 (Clrver.exe) 會報告電腦上已安裝的所有通用語言執行平台 (CLR) 版本。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
clrver [option]  
```  
  
## <a name="options"></a>選項  
  
|選項|說明|  
|------------|-----------------|  
|`-all`|顯示電腦上所有正在使用 CLR 的處理序。|  
|*pid*|顯示具有指定處理序 ID (PID) 的處理序所使用的 CLR 版本。|  
|`-?`|顯示工具的命令語法和選項。|  
  
## <a name="remarks"></a>備註  
 如果您呼叫 Clrver.exe 時未使用任何選項，則會顯示所有已安裝的 CLR 版本。 如果您指定另一個使用者的 PID，則必須具有系統管理權限才能取得版本資訊。  
  
> [!NOTE]
>  在 Windows Vista (含) 以後版本中，使用者帳戶控制 (UAC) 會判斷使用者的權限。 如果您是內建 Administrators 群組的成員，系統會將兩個執行階段存取語彙基元 (Token) 指派給您：標準使用者存取語彙基元及管理員存取語彙基元。 根據預設，您會屬於標準使用者角色。 若要執行需要系統管理權限的程式碼，您必須先將權限從標準使用者提高為系統管理員。 您可以在啟動命令提示字元時以滑鼠右鍵按一下命令提示字元圖示，並表示您要以系統管理員身分執行，藉此提高為系統管理員權限。  
  
 若您嘗試判斷 SYSTEM、LOCAL SERVICE 和 NETWORK SERVICE 處理序的 CLR 版本，系統會顯示一則訊息，表示 PID 不存在。  
  
## <a name="examples"></a>範例  
 下列命令會顯示電腦上安裝的所有 CLR 版本。  
  
 `clrver`  
  
 下列命令會顯示處理序 128 所使用的 CLR 版本。  
  
 `clrver 128`  
  
 下列命令會顯示所有 Managed 處理序及其使用的 CLR 版本。  
  
 `Clrver -all`  
  
## <a name="see-also"></a>另請參閱  
 [工具](../../../docs/framework/tools/index.md)   
 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

