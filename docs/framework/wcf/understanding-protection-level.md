---
title: 了解保護層級
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 0c034608-a1ac-4007-8287-b1382eaa8bf2
ms.openlocfilehash: 90fb844931c3af54367d0e7c14a766636cdcc71a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096045"
---
# <a name="understanding-protection-level"></a>了解保護層級
在許多不同的類別上都可找到 `ProtectionLevel` 屬性，例如 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.OperationContractAttribute> 類別。 此屬性會控制如何保護訊息的部分 (或全部) 內容。 本主題說明 Windows Communication Foundation (WCF) 功能，以及其運作方式。  
  
 如需設定保護層級的指示，請參閱[How to:設定 ProtectionLevel 屬性](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)。  
  
> [!NOTE]
>  保護層級只能在程式碼中加以設定，而不能在組態中設定。  
  
## <a name="basics"></a>基本概念  
 請從下列適當的基本描述來了解保護層級功能：  
  
-   訊息的任何部分都存在三個基本保護層級。 屬性 (無論其出現在任何位置) 會設定為其中一個 <xref:System.Net.Security.ProtectionLevel> 列舉值。 這些值包括如下 (依照遞增的保護順序)：  
  
    -   `None`。  
  
    -   `Sign`。 保護的部分會以數位方式簽署。 這樣可以確保偵測到保護訊息部分所受到的任何竄改。  
  
    -   `EncryptAndSign`。 訊息部分會先加密以確保機密性，接著才進行簽署。  
  
-   您可以設定保護需求僅適用於*應用程式資料*透過這項功能。 例如，WS-Addressing 標頭是基礎結構資料，因此不會受到 `ProtectionLevel` 影響。  
  
-   當安全性模式設定為 `Transport` 時，整個訊息就會由傳輸機制保護。 因此，針對訊息的不同部分設定個別的保護層級不會有任何作用。  
  
-   `ProtectionLevel`可讓開發人員設定*最低層級*繫結必須符合。 當服務完成部署之後，指定於組態中的實際繫結不一定會支援該最低層級。 例如，根據預設，<xref:System.ServiceModel.BasicHttpBinding> 類別不支援安全性 (雖然此選項可加以啟用)。 因此，搭配使用該類別與具有不同於 `None` 之任何設定的合約，將會造成例外狀況 (Exception) 的擲回。  
  
-   如果服務要求的最小`ProtectionLevel`針對所有的訊息是`Sign`，用戶端 （或許是由非 WCF 技術所建立） 可加密並簽署所有訊息 （此為多個所需的最小）。 在此情況下，WCF 不會擲回例外狀況因為用戶端已經超過最小值。 不過請注意，WCF 應用程式 （服務或用戶端） 不會過度保護訊息部分可能的話，但會遵守最低層級。 並請注意，當使用 `Transport` 做為安全性模式時，由於傳輸層級在本質上無法提供更細微層級的安全保護，所以它可能會過度保護訊息資料流。  
  
-   若您明確地將 `ProtectionLevel` 明確設定為 `Sign` 或 `EncryptAndSign`，則您必須使用已啟用安全性的繫結，否則會擲回例外狀況。  
  
-   若您選擇了一個啟用安全性的繫結，卻沒有在合約中設定 `ProtectionLevel` 屬性，則所有應用程式資料都會加密與簽章。  
  
-   若您選擇了尚未啟用安全性的繫結 (例如，根據預設，`BasicHttpBinding` 類別會停用安全性)，又沒有明確設定 `ProtectionLevel`，則所有應用程式資料都不會受到保護。  
  
-   如果您使用在傳輸層級套用安全性的繫結，此時將根據傳輸層級的能力來保護所有的應用程式資料。  
  
-   如果您使用在訊息層級套用安全性的繫結，此時將根據設定於合約中的保護層級來保護應用程式資料。 如果您沒有指定保護層級，則訊息中的所有應用程式資料都會加密和簽署。  
  
-   在不同的範圍層級上皆可設定 `ProtectionLevel`。 範圍設定有相關聯的階層，下一節內容將說明這一點。  
  
## <a name="scoping"></a>範圍設定  
 在最上層 API 設定 `ProtectionLevel`，便會設定其下各層的保護層級。 如果較低層的 `ProtectionLevel` 是設定為不同值，則階層中比該層還低的所有 API 就會重設為新的保護層級 (不過，比該層還高的 API 仍然是受最上層保護層級的影響)。 階層如下所述。 相同一層的屬性屬於對等。  
  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
 <xref:System.ServiceModel.FaultContractAttribute>  
  
 <xref:System.ServiceModel.MessageContractAttribute>  
  
 <xref:System.ServiceModel.MessageHeaderAttribute>  
  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
  
## <a name="programming-protectionlevel"></a>程式設計 ProtectionLevel  
 若要程式設計階層中任何一點的 `ProtectionLevel`，只要在套用屬性 (Attribute) 時將屬性 (Property) 設定為適當值即可。 如需範例，請參閱[如何：設定 ProtectionLevel 屬性](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)。  
  
> [!NOTE]
>  設定錯誤和訊息合約上的屬性時，需要了解這些功能的運作方式。 如需詳細資訊，請參閱[如何：設定 ProtectionLevel 屬性](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)並[使用訊息合約](../../../docs/framework/wcf/feature-details/using-message-contracts.md)。  
  
## <a name="ws-addressing-dependency"></a>WS-Addressing 相依性  
 在大部分情況下，使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來產生用戶端可確保用戶端和服務的合約完全相同。 不過，似乎相同的合約可能會導致用戶端擲回例外狀況。 每當有繫結不支援 WS-Addressing 規格，而且在合約中指定了多重的保護層級時，便會發生這種情形。 例如，當 <xref:System.ServiceModel.BasicHttpBinding> 類別不支援此規格，或是您建立了不支援 WS-Addressing 的繫結。 `ProtectionLevel` 功能必須依賴 WS-Addressing 規格，才能在單一合約上啟用不同的保護層級。 如果繫結不支援 WS-Addressing 規格，則所有的層級都會設定為相同的保護層級。 合約上所有範圍的有效保護層級，都會設定為在合約上使用的最強保護層級。  
  
 這樣便可能造成無法一下子就完成偵錯的問題。 您也可能建立包含適用於一個以上服務之方法的用戶端合約 (介面)。 也就是說，這個相同的介面會用來建立與多個服務通訊的用戶端，而且這個單一介面會包含適用於所有服務的方法。 開發人員在處理此罕見案例時，必須非常謹慎地只叫用個別特定服務所適用的方法。 如果繫結是 <xref:System.ServiceModel.BasicHttpBinding> 類別，就會無法支援多重保護層級。 不過，進行回覆該用戶端的服務可能會採用比需要層級還低的保護層級來回應用戶端。 在此情況下，用戶端會擲回例外狀況，因為它預期的是較高的保護層級。  
  
 下列程式碼範例會說明這個問題。 下例範例會示範服務和用戶端合約。 假設繫結[ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)項目。 因此，合約上的所有作業都具有相同的保護層級。 這個一致的保護層級將被判定為所有作業的最低保護層級。  
  
 服務合約是：  
  
 [!code-csharp[c_ProtectionLevel#7](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#7)]
 [!code-vb[c_ProtectionLevel#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#7)]  
  
 下列程式碼會示範用戶端合約介面。 請注意，其中包含要搭配不同服務使用的 `Tax` 方法：  
  
 [!code-csharp[c_ProtectionLevel#8](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#8)]
 [!code-vb[c_ProtectionLevel#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#8)]  
  
 當用戶端呼叫 `Price` 方法時，它會在從服務接收回覆時擲回例外狀況。 這個例外狀況的發生是因為用戶端沒有在 `ProtectionLevel` 上指定 `ServiceContractAttribute`，使得用戶端對包括 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> 方法的所有方法使用預設值 (`Price`)。 然而，此服務會傳回使用 <xref:System.Net.Security.ProtectionLevel.Sign> 層級的值，因為服務合約會定義將其保護層級設定為 <xref:System.Net.Security.ProtectionLevel.Sign> 的單一方法。 在此情況下，在驗證來自於服務的回應時，用戶端便會擲回錯誤。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageHeaderAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- <xref:System.Net.Security.ProtectionLevel>
- [保護服務的安全](../../../docs/framework/wcf/securing-services.md)
- [HOW TO：設定 ProtectionLevel 屬性](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)
- [指定與處理合約和服務中的錯誤](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [使用訊息合約](../../../docs/framework/wcf/feature-details/using-message-contracts.md)
