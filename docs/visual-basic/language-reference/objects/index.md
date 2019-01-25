---
title: 物件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic]
ms.assetid: 651c73e4-dca8-402b-9c6b-e3902b3a3f4b
ms.openlocfilehash: 59558583a35f83baa953cfc94a17c6c002f91b83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703493"
---
# <a name="objects-visual-basic"></a>物件 (Visual Basic)
本主題提供其他主題的連結，而這些主題記錄 Visual Basic 執行階段物件，並包含其成員程序、屬性和事件的表格。  
  
## <a name="visual-basic-run-time-objects"></a>Visual Basic 執行階段物件  
  
|||  
|---|---|  
|<xref:Microsoft.VisualBasic.Collection>|提供便利的方式，以將一組相關項目當成單一物件來查看。|  
|<xref:Microsoft.VisualBasic.Information.Err%2A>|包含執行階段錯誤的相關資訊。|  
|`My.Application` 物件包含下列類別：<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> 提供適用於所有專案的成員。<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> 提供適用於 Windows Forms 應用程式的成員。<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> 提供適用於主控台應用程式的成員。|提供僅與目前應用程式或 DLL 建立關聯的資料。 使用 `My.Application` 無法改變任何系統層級資訊。<br /><br /> 某些成員僅適用於 Windows Forms 或主控台應用程式。|  
|`My.Application.Info` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Info%2A>)|提供屬性，以取得應用程式相關資訊，例如版本號碼、描述、載入的組件等等。|  
|`My.Application.Log` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>)|提供屬性和方法，以將事件和例外狀況資訊寫入至應用程式的記錄檔接聽程式。|  
|`My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)|提供的屬性，以操作電腦元件，例如音訊、時鐘、鍵盤、檔案系統等等。|  
|`My.Computer.Audio` (<xref:Microsoft.VisualBasic.Devices.Audio>)|提供用於播放音效的方法。|  
|`My.Computer.Clipboard` (<xref:Microsoft.VisualBasic.Devices.Computer.Clipboard%2A>)|提供用於操作剪貼簿的方法。|  
|`My.Computer.Clock` (<xref:Microsoft.VisualBasic.Devices.Clock>)|提供屬性，以從系統時鐘存取目前當地時間與國際標準時間 (相當於格林威治標準時間)。|  
|`My.Computer.FileSystem` (<xref:Microsoft.VisualBasic.FileIO.FileSystem>)|提供屬性和方法，以處理磁碟機、檔案和目錄。|  
|`My.Computer.FileSystem.SpecialDirectories` (<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>)|提供屬性，以存取常用的參考目錄。|  
|`My.Computer.Info` (<xref:Microsoft.VisualBasic.Devices.ComputerInfo>)|提供屬性，以取得電腦的記憶體、已載入組件、名稱和作業系統的相關資訊。|  
|`My.Computer.Keyboard` (<xref:Microsoft.VisualBasic.Devices.Keyboard>)|提供屬性以存取鍵盤目前的狀態，例如目前已按下哪些按鍵，並提供方法將按鍵輸入傳送至使用中視窗。|  
|`My.Computer.Mouse` (<xref:Microsoft.VisualBasic.Devices.Mouse>)|提供屬性，以取得本機電腦上已安裝之滑鼠的格式和組態相關資訊。|  
|`My.Computer.Network` (<xref:Microsoft.VisualBasic.Devices.Network>)|提供屬性、事件和方法，以與電腦所連接的網路互動。|  
|`My.Computer.Ports` (<xref:Microsoft.VisualBasic.Devices.Ports>)|提供屬性和方法，以存取電腦的序列連接埠。|  
|`My.Computer.Registry` (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)|提供屬性和方法，以操作登錄。|  
|[My.Forms 物件](../../../visual-basic/language-reference/objects/my-forms-object.md)|提供屬性，以存取目前專案中所宣告的每個 Windows Form 的執行個體。|  
|`My.Log` (<xref:Microsoft.VisualBasic.Logging.AspLog>)|提供屬性和方法，以將事件和例外狀況資訊寫入應用程式的 Web 應用程式記錄檔接聽程式。|  
|[My.Request 物件](../../../visual-basic/language-reference/objects/my-request-object.md)|取得所要求頁面的 <xref:System.Web.HttpRequest> 物件。 `My.Request` 物件包含目前 HTTP 要求的相關資訊。<br /><br /> `My.Request` 物件僅適用於 [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] 應用程式。|  
|[My.Resources 物件](../../../visual-basic/language-reference/objects/my-resources-object.md)|提供屬性和類別，以存取應用程式的資源。|  
|[My.Response 物件](../../../visual-basic/language-reference/objects/my-response-object.md)|取得與 <xref:System.Web.HttpResponse> 關聯的 <xref:System.Web.UI.Page> 物件。 此物件可讓您將 HTTP 回應資料傳送給用戶端，並包含該回應的相關資訊。<br /><br /> `My.Response` 物件僅適用於 [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] 應用程式。|  
|[My.Settings 物件](../../../visual-basic/language-reference/objects/my-settings-object.md)|提供屬性和方法，以存取應用程式的設定。|  
|`My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>)|提供目前使用者相關資訊的存取權。|  
|[My.WebServices 物件](../../../visual-basic/language-reference/objects/my-webservices-object.md)|提供屬性，以建立和存取目前專案所參考之每個 Web 服務的單一執行個體。|  
|<xref:Microsoft.VisualBasic.FileIO.TextFieldParser>|提供用於剖析結構化文字檔的方法和屬性。|  
  
## <a name="see-also"></a>另請參閱
- [Visual Basic 語言參考](../../../visual-basic/language-reference/index.md)
- [Visual Basic](../../../visual-basic/index.md)
