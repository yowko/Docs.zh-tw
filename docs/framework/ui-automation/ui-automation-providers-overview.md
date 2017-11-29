---
title: "UI 自動化提供者概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
caps.latest.revision: "38"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 4adcc157f4d79898a0418219993681920eb92965
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ui-automation-providers-overview"></a>UI 自動化提供者概觀
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 使用者介面自動化提供者可以讓控制項與使用者介面自動化用戶端應用程式進行通訊。 一般而言， [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 中的每個控制項或其他不同項目都是由提供者表示。 提供者會公開項目的相關資訊並選擇性地實作控制項模式，讓用戶端應用程式與控制項互動。  
  
 用戶端應用程式通常不會直接與提供者搭配使用。 使用 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]、 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]或 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 架構之應用程式中，大多數的標準控制項都會自動公開至 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 系統。 實作自訂控制項的應用程式也會實作那些控制項的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 提供者；因此，用戶端應用程式不需要採取任何特殊步驟，即可加以存取。  
  
 本主題提供控制項開發人員如何實作 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 提供者的概觀，特別是針對 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] 和 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 視窗中的控制項。  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>提供者類型  
 使用者介面自動化提供者分為兩類：用戶端提供者和伺服器端提供者。  
  
### <a name="client-side-providers"></a>用戶端提供者  
 用戶端提供者由使用者介面自動化用戶端實作，以便與不支援或不完全支援 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的應用程式通訊。 用戶端提供者通常會透過傳送和接收 [!INCLUDE[TLA2#tla_win](../../../includes/tla2sharptla-win-md.md)] 訊息，與跨處理序界限的伺服器通訊。  
  
 因為 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]、 [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)]或 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 應用程式之控制項的使用者介面自動化提供者，即屬於作業系統的一部分，所以用戶端應用程式很少會實作自己的提供者，此概觀也不會涵蓋這些提供者的進一步資訊。  
  
### <a name="server-side-providers"></a>伺服器端提供者  
 伺服器端提供者是由自訂控制項或以 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]、 [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)]或 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]以外之使用者介面架構為基礎的應用程式所實作。  
  
 伺服器端提供者會將介面公開至 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 核心系統，與跨處理序邊界的用戶端應用程式通訊，此核心系統之後會接續處理用戶端的要求。  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>使用者介面自動化提供者概念  
 本節提供某些主要概念的簡短說明，讓您了解以便實作使用者介面自動化提供者。  
  
### <a name="elements"></a>項目  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 項目是對使用者介面自動化用戶端顯示的 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 部分。 範例包含應用程式視窗、窗格、按鈕、工具提示、清單方塊和清單項目。  
  
### <a name="navigation"></a>巡覽  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 項目是以 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的形式公開至用戶端。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 會在項目之間巡覽以建構樹狀結構。 巡覽功能是由每個項目的提供者啟用，每個提供者各指向父代、同層級和子系。  
  
 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構用戶端檢視的詳細資訊，請參閱 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)。  
  
### <a name="views"></a>檢視  
 用戶端可在三個主要檢視中檢視 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構，如下表所示。  
  
|||  
|-|-|  
|未經處理的檢視|包含所有項目。|  
|控制項檢視|包含做為控制項的項目。|  
|內容檢視|包含擁有內容的項目。|  
  
 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構用戶端檢視的詳細資訊，請參閱 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)。  
  
 提供者實作負責將項目定義為內容項目或控制項項目。 控制項不一定是內容項目，但所有的內容項目都會是控制項項目。  
  
### <a name="frameworks"></a>架構  
 架構是一個元件，管理該畫面區域的子控制項、點擊測試和呈現。 例如， [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 視窗，通常是指 HWND，可做為包含多個 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 項目 (例如功能表列、狀態列和按鈕) 的架構。  
  
 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] 容器控制項 (例如清單方塊和樹狀結構檢視) 都會被視為架構，因為他們都包含自己的程式碼，以呈現子項目並在其上執行點擊測試。 相對地， [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 清單方塊就不是架構，因為呈現和點擊測試是由其中包含的 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 視窗所處理。  
  
 應用程式中的 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 可由不同架構組成。 例如，HWND 應用程式視窗可能包含 [!INCLUDE[TLA#tla_dhtml](../../../includes/tlasharptla-dhtml-md.md)] ，會依序在 HWND 中包含下拉式方塊此類的元件。  
  
### <a name="fragments"></a>片段  
 片段是來自特定架構之項目的完整子樹狀結構。 子樹狀結構之根目錄節點的項目稱為片段根目錄。 片段根目錄沒有父代，但會裝載於某些其他架構內，通常是 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] 視窗 (HWND)。  
  
### <a name="hosts"></a>主機  
 每個片段的根節點都必須裝載在項目內，而這個項目通常是 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 視窗 (HWND)。 例外狀況是桌面，桌面並沒有裝載於任何其他項目中。 自訂控制項的裝載是控制項本身的 HWND，而非應用程式視窗或任何其他可能包含最上層控制項群組的視窗。  
  
 片段的裝載對於提供 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 服務扮演重要角色， 可在片段根目錄中進行巡覽並提供某些預設屬性，讓自訂提供者不需要進行實作。  
  
## <a name="see-also"></a>另請參閱  
 [伺服器端 UI 自動化提供者實作](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
