---
title: 用戶端 UI 自動化提供者實作
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
ms.openlocfilehash: 50d7921f1c63580248b562864f9c1f398d41c9bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180262"
---
# <a name="client-side-ui-automation-provider-implementation"></a>用戶端 UI 自動化提供者實作
> [!NOTE]
> 這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 微軟作業系統[!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]中正在使用幾個不同的框架，包括 Win32、Windows 表單和[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]。 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 會公開使用者介面項目相關資訊給用戶端。 不過， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 本身不會知道這些架構中存在的不同控制項類型，也不具備從這些架構中擷取資訊的必要技術。 它會將這項工作交給稱為提供者的物件。 提供者會從特定控制項擷取資訊，並將該資訊傳遞給 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，再由它以一致的方式呈現給用戶端。  
  
 提供者可以存在於伺服器端或用戶端上。 伺服器端的提供者是由控制項本身所實作。 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 項目會實作提供者，任何撰寫時考慮到 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的協力廠商控制項也可以實作提供者。  
  
 但是，較舊的控制項（如 Win32 和 Windows 表單中的控制項[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]）並不直接支援 。 這些控制項會改由存在於用戶端處理序並使用跨處理序通訊 (例如，藉由監視控制項的往來視窗訊息) 來取得控制項相關資訊的提供者服務。 這種用戶端提供者有時稱為 Proxy。  
  
 Windows Vista 為標準 Win32 和 Windows 表單控制項提供提供程式。 此外，回退提供程式為未由其他[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]伺服器端提供程式或代理提供但具有 Microsoft 活動協助工具實現的任何控制項提供部分支援。 所有這些提供者都會自動載入，供用戶端應用程式使用。  
  
 有關支援 Win32 和 Windows 表單控制項的詳細資訊，請參閱[標準控制項的 UI 自動化支援](ui-automation-support-for-standard-controls.md)。  
  
 應用程式也可以註冊其他用戶端提供者。  
  
<a name="Distributing_Client-Side_Providers"></a>
## <a name="distributing-client-side-providers"></a>散發用戶端提供者  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 會預期在 Managed 程式碼組件中找到用戶端提供者。 這個組件中的命名空間應該和組件同名。 例如，稱為 ContosoProxies.dll 的組件會包含 ContosoProxies 命名空間。 在命名空間中，建立 <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> 類別。 在靜態 <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> 欄位的實作中，建立用於說明提供者的 <xref:System.Windows.Automation.ClientSideProviderDescription> 結構陣列。  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>
## <a name="registering-and-configuring-client-side-providers"></a>註冊及設定用戶端提供者  
 動態連結程式庫 （DLL） 中的用戶端提供程式通過調用<xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>載入。 用戶端應用程式不需進一步的動作，即可使用提供者。  
  
 藉由使用 <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>，註冊用戶端本身程式碼中實作的提供者。 這個方法會採用 <xref:System.Windows.Automation.ClientSideProviderDescription> 結構陣列做為引數，每個結構會指定下列屬性：  
  
- 回呼函式，會建立提供者物件。  
  
- 提供者將服務之控制項的類別名稱。  
  
- 提供者將服務之應用程式的映像名稱 (通常是可執行檔的完整名稱)。  
  
- 管理類別名稱與目標應用程式中找到之視窗類別比對方式的旗標。  
  
 最後兩個參數為選擇性的。 當用戶端要針對不同應用程式使用不同提供者時，它可以指定目標應用程式的映像名稱。 例如，用戶端可能將一個提供程式用於支援多視圖模式的已知應用程式中的 Win32 清單視圖控制項，而另一個提供程式用於不支援該模式的另一個已知應用程式中的類似控制項。  
  
## <a name="see-also"></a>另請參閱

- [建立用戶端 UI 自動化提供者](create-a-client-side-ui-automation-provider.md)
- [在用戶端應用程式中實作 UI 自動化提供者](implement-ui-automation-providers-in-a-client-application.md)
