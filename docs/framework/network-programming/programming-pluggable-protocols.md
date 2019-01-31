---
title: 可插式通訊協定程式設計
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, pluggable protocols
- WebRequest class, pluggable protocols
- response to Internet request, pluggable protocols
- WebResponse class, pluggable protocols
- sending data, pluggable protocols
- network resources, pluggable protocols
- Internet, pluggable protocols
- programming pluggable protocols
- pluggable protocols, programming
- requesting data from Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 66ef8456-7576-4e97-8956-959b216373db
ms.openlocfilehash: 1becdc227995064a3f34d712834ab358cc41754b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646590"
---
# <a name="programming-pluggable-protocols"></a>可插式通訊協定程式設計
抽象 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 類別提供可插式通訊協定的基底。 透過從 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 衍生通訊協定特定類別，應用程式可以要求來自網際網路資源的資料，並讀取回應，而不需要指定所要使用的通訊協定。  
  
 建立通訊協定特定 <xref:System.Net.WebRequest> 之前，您必須先註冊 Create 方法。 使用 <xref:System.Net.WebRequest> 的靜態 <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> 方法來註冊 <xref:System.Net.WebRequest> 子系，以處理對特定網際網路配置、配置和伺服器或者配置、伺服器和路徑的一組要求。  
  
 在大部分情況下，您將可以使用 <xref:System.Net.WebRequest> 類別的方法和屬性來傳送和接收資料。 不過，如果您需要存取通訊協定特定屬性，則可以將 <xref:System.Net.WebRequest> 類型轉換為特定衍生類別執行個體。  
  
 若要善用可插式通訊協定，<xref:System.Net.WebRequest> 子系必須提供不需要設定通訊協定特定屬性的預設要求和回應交易。 例如，實作 <xref:System.Net.WebRequest> 類別以進行 HTTP 的 <xref:System.Net.HttpWebRequest> 類別預設會提供 `GET` 要求，並傳回包含從網頁伺服器傳回之資料流的 <xref:System.Net.HttpWebResponse>。  
  
## <a name="see-also"></a>另請參閱
- [衍生自 WebRequest](../../../docs/framework/network-programming/deriving-from-webrequest.md)
- [衍生自 WebResponse](../../../docs/framework/network-programming/deriving-from-webresponse.md)
- [以 .NET Framework 進行網路程式設計](../../../docs/framework/network-programming/index.md)
- [如何：轉換 WebRequest 類型以存取通訊協定特定屬性](../../../docs/framework/network-programming/how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
