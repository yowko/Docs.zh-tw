---
title: HOW TO：建立 Windows 服務
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: 514675b3c3ce1f6701dff571361df672fb520c6a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053663"
---
# <a name="how-to-create-windows-services"></a>作法：建立 Windows 服務
當您建立服務時，可以使用稱為 **Windows 服務**的 Visual Studio 專案範本。 這個範本會透過參考適當的類別和命名空間、設定繼承自服務的基底類別，以及覆寫您可能想要覆寫的其中幾個方法，來自動為您執行大部分的工作。  
  
> [!WARNING]
> 您無法在 Express 版的 Visual Studio 中使用 Windows 服務專案範本。  
  
 若要建立可運作的服務，您必須至少：  
  
- 設定 <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> 屬性。  
  
- 建立服務應用程式的必要安裝程式。  
  
- 覆寫並指定 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 方法的程式碼，以自訂服務的運作方式。  
  
### <a name="to-create-a-windows-service-application"></a>建立 Windows 服務應用程式  
  
1. 建立 **Windows 服務**專案。  
  
    > [!NOTE]
    > 如需不使用範本來撰寫服務的指示，請參閱[如何：以程式設計方式撰寫服務](how-to-write-services-programmatically.md)。  
  
2. 在 [屬性] 視窗中，設定服務的 <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> 屬性。  
  
     ![設定 ServiceName 屬性。](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")  
  
    > [!NOTE]
    > <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> 屬性的值必須一律符合安裝程式類別中所記錄的名稱。 如果您變更這個屬性，也必須更新安裝程式類別的 <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> 屬性。  
  
3. 設定下列任何屬性，以決定服務的運作方式。  
  
    |屬性|設定|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|如果為 `True`，則表示服務會接受停止執行的要求；如果為 `false`，則不會停止服務。|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|如果為 `True`，則表示當服務所在的電腦關機時，服務想要收到通知，以便呼叫 <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> 程序。|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|如果為 `True`，則表示服務會接受暫停或繼續執行的要求；如果為 `false`，則表示不會暫停及繼續服務。|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|`True` 表示服務可以處理電腦電源狀態變更的通知；`false` 則會防止服務收到這些變更的通知。|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|如果為 `True`，則會在服務執行動作時，將資訊項目寫入應用程式事件記錄檔；如果為 `false`，則會停用這項功能。 如需詳細資訊，請參閱[如何：記錄關於服務的資訊](how-to-log-information-about-services.md)。 **注意：** 依預設，<xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 會設為 `true`。|  
  
    > [!NOTE]
    > 當 <xref:System.ServiceProcess.ServiceBase.CanStop%2A> 或 <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> 設定為 `false` 時，**服務控制管理員**將會停用對應的功能表選項，以停止、暫停或繼續服務。  
  
4. 存取程式碼編輯器，然後填入您想要對 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 程序進行的處理。  
  
5. 覆寫您想要定義功能的其他任何方法。  
  
6. 為服務應用程式加入必要的安裝程式。 如需詳細資訊，請參閱[如何：將安裝程式新增至服務應用程式](how-to-add-installers-to-your-service-application.md)。  
  
7. 從 [建置] 功能表選取 [建置方案]，以建置您的專案。  
  
    > [!NOTE]
    > 請勿按 F5 執行您的專案，您無法透過這個方法來執行服務專案。  
  
8. 安裝服務。 如需詳細資訊，請參閱[如何：安裝和解除安裝服務](how-to-install-and-uninstall-services.md)。  
  
## <a name="see-also"></a>另請參閱

- [Windows 服務應用程式簡介](introduction-to-windows-service-applications.md)
- [如何：以程式設計方式撰寫服務](how-to-write-services-programmatically.md)
- [如何：將安裝程式新增至服務應用程式](how-to-add-installers-to-your-service-application.md)
- [如何：記錄關於服務的資訊](how-to-log-information-about-services.md)
- [如何：啟動服務](how-to-start-services.md)
- [如何：指定服務的資訊安全內容](how-to-specify-the-security-context-for-services.md)
- [如何：安裝和解除安裝服務](how-to-install-and-uninstall-services.md)
- [逐步解說：在元件設計工具中建立 Windows 服務應用程式](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
