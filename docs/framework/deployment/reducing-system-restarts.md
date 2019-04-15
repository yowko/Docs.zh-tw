---
title: 在 .NET Framework 4.5 安裝期間減少系統重新啟動的次數
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, reducing system restarts
- installing .NET Framework
- installation [.NET Framework]
ms.assetid: 7aa8cb72-dee9-4716-ac54-b17b9ae8218f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b7e8a4d92661b974fba7c88989891b30e54e94d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218442"
---
# <a name="reducing-system-restarts-during-net-framework-45-installations"></a>在 .NET Framework 4.5 安裝期間減少系統重新啟動的次數
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 安裝程式會使用[重新啟動管理員](https://go.microsoft.com/fwlink/?LinkId=231425)，盡可能在安裝時防止系統重新啟動。 如果您的應用程式安裝程式安裝 .NET Framework，則可以與 [重新啟動管理員] 互動來利用這項功能。 如需詳細資訊，請參閱[如何：取得 .NET Framework 4.5 安裝程式的進度](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)。  
  
## <a name="reasons-for-a-restart"></a>重新啟動的原因  
 如果在安裝期間正在使用 .NET Framework 4 應用程式，則 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 安裝需要重新啟動系統。 這是因為 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 會取代 .NET Framework 4 檔案，並且需要這些檔案可在安裝期間使用。 在許多情況下，事先偵測和關閉正在使用的 .NET Framework 4 應用程式，即可避免重新啟動。 不過，不應該關閉部分系統應用程式。 在這些情況下，無法避免重新啟動。  
  
## <a name="end-user-experience"></a>一般使用者體驗  
 如果安裝程式偵測到正在使用 .NET Framework 4 應用程式，執行完整 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 安裝的一般使用者就有機會可以避免重新啟動系統。 訊息會列出所有執行中 .NET Framework 4 應用程式，並提供選項來關閉這些應用程式，再進行安裝。 如果使用者確認，則安裝程式會關閉這些應用程式，並避免重新啟動系統。 如果使用者在一段時間內未回應訊息，則會繼續安裝，而不需要關閉任何應用程式。  
  
 如果 [重新啟動管理員] 偵測到即使關閉執行中應用程式也需要重新啟動系統的情況，則不會顯示訊息。  
  
 ![關閉應用程式對話方塊](../../../docs/framework/deployment/media/closeapplicationdialog.png "CloseApplicationDialog")  
提示關閉正在使用的 .NET Framework 應用程式  
  
## <a name="using-a-chained-installer"></a>使用鏈結的安裝程式  
 如果您想要轉散發 .NET Framework 與應用程式，但想要使用自己的安裝程式和 UI，則可以在安裝程序中包括 (鏈結) .NET Framework 安裝程序。 如需鏈結之安裝的詳細資訊，請參閱[開發人員部署手冊](../../../docs/framework/deployment/deployment-guide-for-developers.md)。 為了減少在鏈結的安裝中重新啟動系統，.NET Framework 安裝程式會將要關閉的應用程式清單提供給安裝程式。 安裝程式必須透過使用者介面 (例如訊息方塊) 將這項資訊提供給使用者，並取得使用者的回應，然後將回應傳遞回 .NET Framework 安裝程式。 如需所鏈結安裝程式的範例，請參閱[如何：取得 .NET Framework 4.5 安裝程式的進度](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)一文。  
  
 如果您要使用鏈結的安裝程式，但不想要提供關閉應用程式的專屬訊息方塊，則可以在鏈結 .NET Framework 安裝程序時，於命令列上使用 `/showrmui` 和 `/passive` 選項。 當您一起使用這些選項時，安裝程式會顯示關閉可關閉之應用程式的訊息方塊，以避免重新啟動系統。 被動模式下之這個訊息方塊的行為與完整使用者介面的作用相同。 如需 .NET Framework 可轉散發套件的完整一組命令列選項，請參閱[開發人員部署手冊](../../../docs/framework/deployment/deployment-guide-for-developers.md)。  
  
## <a name="see-also"></a>另請參閱

- [部署](../../../docs/framework/deployment/index.md)
- [開發人員部署手冊](../../../docs/framework/deployment/deployment-guide-for-developers.md)
- [作法：取得 .NET Framework 4.5 安裝程式的進度](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
