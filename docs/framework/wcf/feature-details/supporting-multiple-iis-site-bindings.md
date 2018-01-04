---
title: "支援多重 IIS 網站繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8dcd6a5e6204b1a629c1ee1e2ddfb9b263fa8054
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="supporting-multiple-iis-site-bindings"></a>支援多重 IIS 網站繫結
在網際網路資訊服務 (IIS) 7.0 之下裝載 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務時，您可能需要提供在相同網站使用相同通訊協定的多個基底位址。 這樣可讓相同的服務回應數個不同的 URI。 當您要裝載在 http://www.contoso.com 和 http://contoso.com 接聽的服務時，這種方式就會很有用。當您所建立的服務具有內部使用者基底位址，同時具有外部使用者個別基底位址時，也適用此方式。 例如：http://internal.contoso.com 和 http://www.contoso.com。  
  
> [!NOTE]
>  不過這個功能僅適用於 HTTP 通訊協定。  
  
## <a name="multiple-base-addresses"></a>多個基底位址  
 只有在 IIS 之下裝載的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務才能使用這項功能。 預設不會啟用此功能。 若要啟用它，您必須加入`multipleSiteBindingsEnabled`屬性加入 <`serviceHostingEnvironment`> 在 Web.config 中的項目檔案，並將它設定為`true`，如下列範例所示。  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 在 IIS 之下裝載 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務時，IIS 會根據 URI 建立一個基底位址，並加入至含有應用程式的虛擬目錄中。 您可以使用 Internet Information Services 管理員，加入其他使用相同通訊協定的基底位址，以便在網站中加入一個或多個繫結。 為每個繫結指定通訊協定 (HTTP 或 HTTPS)、IP 位址、連接埠和主機名稱。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]使用 Internet Information Services 管理員，請參閱[IIS 管理員 (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164057)。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]加入繫結至站台，請參閱[建立網站 (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164060)  
  
 為相同網站指定多個基底位址會影響 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [說明] 頁面的內容、匯入結構描述，以及由服務所產生的 WSDL/MEX 資訊。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [說明] 頁面會顯示命令列，可用於產生與服務進行通訊的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端。 此命令列僅包含在 IIS 繫結中指定的第一個網站位址。 同樣地，在匯入結構時，只會使用在 IIS 繫結中指定的第一個基底位址。 WSDL 和 MEX 資料包含所有在 IIS 繫結中指定的基底位址。  
  
> [!WARNING]
>  這表示如果服務擁有兩個基底位址，一個用於內部使用者，另一個用於外部使用者，則會在由服務所產生的 WSDL/MEX 資訊中指定這兩個位址。
