---
title: Aximp.exe (Windows Form ActiveX 控制項匯入工具)
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls, hosting in Windows Forms
- ActiveX Control Importer
- type definitions, converting
- Aximp.exe
- Windows Forms ActiveX Control Importer
ms.assetid: 482c0d83-7144-4497-b626-87d2351b78d0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71e06f8e42e4ca6da80286c9aa329ee99b02fcf4
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222138"
---
# <a name="aximpexe-windows-forms-activex-control-importer"></a>Aximp.exe (Windows Form ActiveX 控制項匯入工具)
ActiveX 控制項匯入工具可以將 ActiveX 控制項在 COM 類型程式庫中的類型定義，轉換成 Windows Form 控制項。  
  
 Windows Form 只能裝載 Windows Form 控制項，也就是衍生自 <xref:System.Windows.Forms.Control> 的類別。 Aximp.exe 會產生 ActiveX 控制項的包裝函式類別，可以在 Windows Form 上裝載。 這可讓您使用相同的設計階段支援和程式設計方法論，以適用於其他 Windows Form 控制項。  
  
 若要裝載 ActiveX 控制項，您必須產生衍生自 <xref:System.Windows.Forms.AxHost> 的包裝函式控制項。 這個包裝函式控制項包含基礎 ActiveX 控制項的執行個體。 它知道如何與 ActiveX 控制項進行通訊，但是會顯示為 Windows Form 控制項。 這個產生的控制項會裝載 ActiveX 控制項並公開其屬性、方法和事件，如同這些產生的控制項。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
aximp [options]{file.dll | file.ocx}  
```  
  
## <a name="remarks"></a>備註  
  
|引數|說明|  
|--------------|-----------------|  
|*file*|原始程式檔的名稱，包含要轉換的 ActiveX 控制項。 檔案引數必須有 .dll 或 .ocx 副檔名。|  
  
|選項|說明|  
|------------|-----------------|  
|`/delaysign`|指定 Aximp.exe 使用延遲簽署來簽署產生的控制項。 您必須使用 `/keycontainer:`、`/keyfile:` 或 `/publickey:` 選項來指定此選項。 如需延遲簽署程序的詳細資訊，請參閱[延遲簽署組件](../../../docs/framework/app-domains/delay-sign-assembly.md)。|  
|`/help`|顯示工具的命令語法和選項。|  
|`/keycontainer:` *containerName*|使用 *containerName* 所指定之金鑰容器中的公開/私密金鑰組，以強式名稱簽署產生的控制項。|  
|`/keyfile:` *filename*|使用 *filename* 中找到的發行者正式公開/私密金鑰組，以強式名稱簽署產生的控制項。|  
|`/nologo`|隱藏 Microsoft 程式啟始資訊顯示。|  
|`/out:` *filename*|指定要建立的組件名稱。|  
|`/publickey:` *filename*|使用由 *filename* 所指定之檔案中找到的公開金鑰，以強式名稱簽署產生的控制項。|  
|`/rcw:` *filename*|使用指定的執行階段可呼叫包裝函式，而不是產生新的執行階段可呼叫包裝函式。 您可以指定多個執行個體。 目前的目錄用於相對路徑。 如需詳細資訊，請參閱[執行階段可呼叫包裝函式](../../../docs/framework/interop/runtime-callable-wrapper.md)。|  
|`/silent`|隱藏顯示成功訊息。|  
|`/source`|產生 Windows Form 包裝函式的 C# 原始程式碼。|  
|`/verbose`|指定詳細資訊模式；顯示其他進度資訊。|  
|`/?`|顯示工具的命令語法和選項。|  
  
 Aximp.exe 會一次轉換整個 ActiveX 控制項類型程式庫並產生一組組件，其中包含通用語言執行平台中繼資料，並控制原始類型程式庫中定義之類型的實作。 根據下列模式為產生的檔案命名：  
  
 適用於 COM 類型的 Common Language Runtime Proxy：*progid*.dll  
  
 適用於 ActiveX 控制項的 Windows Forms Proxy (其中 Ax 代表 ActiveX)：Ax*progid*.dll  
  
> [!NOTE]
>  如果 ActiveX 控制項的成員名稱符合 .NET Framework 中定義的名稱，則 Aximp.exe 在建立 AxHost 衍生類別時就會在成員名稱前面加上 "Ctl"。 例如，如果您的 ActiveX 控制項有一個名為 "Layout" 的成員，它在 AxHost 衍生類別中就會被重新命名為 "CtlLayout"，因為 Layout 事件是在 .NET Framework 中定義的。  
  
 您可以使用 [Ildasm.exe (IL 反組譯工具)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 這類工具，檢查這些產生的檔案。  
  
 不支援使用 Aximp.exe 來產生 ActiveX WebBrowser 控制項 (shdocvw.dll) 的 .NET 組件。  
  
 當您在 shdocvw.dll 上執行 Aximp.exe 時，必定會在執行這個工具的目錄中建立另一個名為 shdocvw.dll 的檔案。 如果這個產生的檔案是置於 Documents and Settings 目錄中，它將會對 Microsoft Internet Explorer 和 Windows 檔案總管造成問題。 當電腦重新開機時，Windows 會在搜尋 system32 目錄之前，先在 Documents and Settings 目錄中尋找 shdocvw.dll 的複本。 它會使用在 Documents and Settings 目錄中找到的複本，並嘗試載入 Managed 包裝函式。 Internet Explorer 和 Windows 檔案總管將無法正常運作，因為它們必須依賴位於 system32 目錄中之 shdocvw.dll 版本中的轉譯引擎。 如果發生這種問題，請刪除 Documents and Settings 目錄中的 shdocvw.dll 複本，然後重新啟動電腦。  
  
 使用 Aximp.exe 搭配 shdocvw.dll 來建立用於應用程式開發的 .NET 組件時，可能也會導致問題。 在這種情況下，您的應用程式將會載入 shdocvw.dll 的系統版本和產生的版本，而且系統版本具有優先權。 在這個情況下，當您試圖將 Web 網頁載入到 WebBrowser ActiveX 控制項內部時，系統會以 [開啟/儲存] 對話方塊提示使用者。 當使用者按一下 [開啟] 時，將會在 Internet Explorer 中開啟網頁。 這種情形只會在使用執行 Internet Explorer 第 6 版 (含) 以前版本的電腦上發生。 若要避免這個問題，請使用受控 <xref:System.Windows.Forms.WebBrowser> 控制項或使用 Visual Studio 來產生受控 shdocvw.dll，如以下連結所述：[如何：將參考新增至類型程式庫](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md)。  
  
## <a name="example"></a>範例  
 下列命令會產生 Media Player 控制項 `msdxm.ocx` 的 MediaPlayer.dll 和 AxMediaPlayer.dll。  
  
```  
aximp c:\systemroot\system32\msdxm.ocx  
```  
  
## <a name="see-also"></a>請參閱  
 [工具](../../../docs/framework/tools/index.md)  
 [Ildasm.exe (IL 反組譯工具)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
