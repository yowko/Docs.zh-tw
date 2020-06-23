---
title: 支援多重 IIS 網站繫結
description: 瞭解在 IIS 中裝載 WCF 服務時，如何提供在相同網站上使用相同通訊協定的多個基底位址。
ms.date: 03/30/2017
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
ms.openlocfilehash: 290dca03dbed7d0a7442a3903b735eb189929ed1
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244864"
---
# <a name="supporting-multiple-iis-site-bindings"></a>支援多重 IIS 網站繫結
在 Internet Information Services （IIS）7.0 下裝載 Windows Communication Foundation （WCF）服務時，您可能會想要在相同的網站上提供多個使用相同通訊協定的基底位址。 這樣可讓相同的服務回應數個不同的 URI。 當您想要裝載在和上接聽的服務時，這會很有用 `http://www.contoso.com` `http://contoso.com` 。 當您所建立的服務具有內部使用者基底位址，同時具有外部使用者個別基底位址時，也適用此方式。 例如：`http://internal.contoso.com` 和 `http://www.contoso.com`。  
  
> [!NOTE]
> 不過這個功能僅適用於 HTTP 通訊協定。  
  
## <a name="multiple-base-addresses"></a>多個基底位址  
 這項功能僅適用于在 IIS 底下裝載的 WCF 服務。 預設不會啟用此功能。 若要啟用它，您必須將 `multipleSiteBindingsEnabled` 屬性加入至 `serviceHostingEnvironment` Web.config 檔案中的 <> 元素，並將它設定為 `true` ，如下列範例所示。  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 在 IIS 下裝載 WCF 服務時，IIS 會根據包含應用程式之虛擬目錄的 URI，為您建立一個基底位址。 您可以使用 Internet Information Services 管理員，加入其他使用相同通訊協定的基底位址，以便在網站中加入一個或多個繫結。 為每個繫結指定通訊協定 (HTTP 或 HTTPS)、IP 位址、連接埠和主機名稱。 如需使用 Internet Information Services 管理員的詳細資訊，請參閱[Iis 管理員（iis 7）](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753842(v=ws.10))。 如需將系結加入至網站的詳細資訊，請參閱[建立網站（IIS 7）](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772350(v=ws.10))  
  
 為相同網站指定多個基底位址會影響 WCF 說明頁面的內容、匯入架構，以及服務所產生的 WSDL/MEX 資訊。 [WCF 說明] 頁面會顯示用來產生可與服務進行通訊之 WCF 用戶端的命令列。 此命令列僅包含在 IIS 繫結中指定的第一個網站位址。 同樣地，在匯入結構時，只會使用在 IIS 繫結中指定的第一個基底位址。 WSDL 和 MEX 資料包含所有在 IIS 繫結中指定的基底位址。  
  
> [!WARNING]
> 這表示如果服務擁有兩個基底位址，一個用於內部使用者，另一個用於外部使用者，則會在由服務所產生的 WSDL/MEX 資訊中指定這兩個位址。
