---
title: Windows 市集應用程式的網路隔離
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 97096d6fa41cd25a92c23cd47008b33fb6037190
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195403"
---
# <a name="network-isolation-for-windows-store-apps"></a>Windows 市集應用程式的網路隔離
<xref:System.Net>、<xref:System.Net.Http> 和 <xref:System.Net.Http.Headers> 命名空間中的類別可以用來開發 Windows 市集應用程式或傳統型應用程式。 在 Windows 市集應用程式中使用時，這些命名空間中的類別受到網路隔離的影響，而網路隔離是 [!INCLUDE[win8](../../../includes/win8-md.md)] 所使用應用程式安全性模型的一部分。 必須在 Windows 市集應用程式的應用程式資訊清單中啟用適當的網路功能，讓系統允許網路存取。  
  
## <a name="checklist-for-network-isolation"></a>網路隔離的檢查清單  
 使用此檢查清單，確定已設定 Windows 市集應用程式的網路隔離。  
  
1.  決定應用程式所需的網路存取要求方向。 這可以是輸出用戶端起始的要求或輸入未經要求的要求，或是這兩種網路要求類型的組合。  
  
2.  判斷該應用程式將與其通訊的網路資源類型。 應用程式可能需要與家用或工作場所網路上受信任的資源進行通訊。 應用程式可能需要與網際網路上的資源進行通訊。 應用程式可能需要存取這兩種類型的網路資源。  
  
3.  在應用程式資訊清單中設定最低必要網路隔離功能。  
  
4.  部署和執行應用程式，以使用針對疑難排解所提供的網路隔離工具對其進行測試。  
  
 如需如何設定用於針對網路隔離進行疑難排解之網路功能和隔離工具的詳細資訊，請參閱 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 開發人員文件中的[如何設定網路隔離功能](https://go.microsoft.com/fwlink/?LinkID=228265)。  
  
## <a name="see-also"></a>請參閱  
 [連線至 Web 服務](https://go.microsoft.com/fwlink/?LinkID=245696)  
 [網路隔離的方針和檢查清單](https://go.microsoft.com/fwlink/?LinkID=228265)  
 [快速入門：使用 HttpClient 進行連線](https://go.microsoft.com/fwlink/?LinkId=245697)  
 [如何使用 HttpClient 處理常式](https://go.microsoft.com/fwlink/?LinkId=245699)  
 [如何保護 HttpClient 連線](https://go.microsoft.com/fwlink/?LinkId=245698)  
 [HttpClient 範例](https://go.microsoft.com/fwlink/?LinkId=242550)
