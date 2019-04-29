---
title: 支援多重 IIS 網站繫結
ms.date: 03/30/2017
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
ms.openlocfilehash: 5a8b06d86b505452f9ded808f727343b1453e592
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696102"
---
# <a name="supporting-multiple-iis-site-bindings"></a>支援多重 IIS 網站繫結
裝載時的網際網路資訊服務 (IIS) 7.0 下的 Windows Communication Foundation (WCF) 服務，您可能想要提供相同的站台使用相同的通訊協定的多個基底位址。 這樣可讓相同的服務回應數個不同的 URI。 這是很有用，當您想要裝載服務，可接聽`http://www.contoso.com`和`http://contoso.com`。 當您所建立的服務具有內部使用者基底位址，同時具有外部使用者個別基底位址時，也適用此方式。 例如：`http://internal.contoso.com`和`http://www.contoso.com`。  
  
> [!NOTE]
>  不過這個功能僅適用於 HTTP 通訊協定。  
  
## <a name="multiple-base-addresses"></a>多個基底位址  
 只有在 IIS 之下裝載的 WCF 服務使用這項功能。 預設不會啟用此功能。 若要啟用它，您必須新增`multipleSiteBindingsEnabled`屬性設定為 <`serviceHostingEnvironment`> 您的 Web.config 中的項目檔案，並將它設定為`true`，如下列範例所示。  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 當裝載在 IIS 下的 WCF 服務，IIS 會為您的虛擬目錄，包含應用程式的 URI 為基礎建立一個基底位址。 您可以使用 Internet Information Services 管理員，加入其他使用相同通訊協定的基底位址，以便在網站中加入一個或多個繫結。 為每個繫結指定通訊協定 (HTTP 或 HTTPS)、IP 位址、連接埠和主機名稱。 如需使用 Internet Information Services 管理員的詳細資訊，請參閱 < [IIS 管理員 (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=164057)。 如需新增繫結至站台的詳細資訊，請參閱[建立網站 (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=164060)  
  
 指定相同的站台的多個基底位址會影響內容 WCF 說明頁面，匯入結構描述，以及服務所產生的 WSDL/MEX 資訊。 WCF 說明頁面會顯示命令列用來產生 WCF 用戶端可與服務通訊。 此命令列僅包含在 IIS 繫結中指定的第一個網站位址。 同樣地，在匯入結構時，只會使用在 IIS 繫結中指定的第一個基底位址。 WSDL 和 MEX 資料包含所有在 IIS 繫結中指定的基底位址。  
  
> [!WARNING]
>  這表示如果服務擁有兩個基底位址，一個用於內部使用者，另一個用於外部使用者，則會在由服務所產生的 WSDL/MEX 資訊中指定這兩個位址。
