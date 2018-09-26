---
title: '&lt;soapProcessing&gt;'
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 296993f1a91a6da93f01610357f35dac4cfab9e6
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47210135"
---
# <a name="ltsoapprocessinggt"></a>&lt;soapProcessing&gt;

定義用戶端端點行為，這個行為會用來封送處理不同繫結型別和訊息版本之間的訊息。

**\<系統。ServiceModel >**   
&nbsp;&nbsp;**\<行為 >**   
&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors >**   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<行為 >**   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing >**

## <a name="syntax"></a>語法

```xml
<soapProcessing processMessages="true|false" />
```

## <a name="attributes-and-elements"></a>屬性和元素

下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|                   | 描述 |
| ----------------- | ----------- |
| `processMessages` | 布林值，這個值指定是否應該在 SOAP 訊息版本之間封送處理訊息。 |

### <a name="child-elements"></a>子元素

無

### <a name="parent-elements"></a>父元素

|     | 描述 |
| --- | ----------- |
| [**\<行為 >**](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) | 指定端點行為。 |

## <a name="remarks"></a>備註

SOAP 處理是在訊息版本之間轉換訊息的程序。

Windows Communication Foundation (WCF) 路由服務可以將訊息從一種通訊協定轉換到另一個。 如果傳入及傳出的訊息版本不同，會建立正確版本的新訊息。 在 <xref:System.ServiceModel.Channels.MessageVersion> 之間處理訊息，是透過建構包含來自傳入 WCF 訊息的主體部分和相關標頭的新 WCF 訊息來完成。 定址專用或是在路由器層級辨識的標頭，不會在建構新 WCF 訊息期間使用，因為這些標頭不是屬於不同的版本 (若為定址標頭)，就是已做為用戶端和路由器之間通訊的一部分處理。

標頭是否放置在傳出訊息內，是透過標頭是否在通過傳入通道層時標記為辨識所決定。 未經辨識的標題 (例如自訂標題) 不會被移除，因此會透過複製到傳出訊息中的方式通過路由服務。 訊息的主體會複製到傳出訊息中。 接著，會將訊息傳出到輸出通道，此時會建立並加入該通訊協定/傳輸專用的所有標題和其他封套資料。

此類處理步驟會在指定 SOAP 處理行為時發生。 這[ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md)行為是端點行為，路由服務啟動時，會套用至所有的用戶端 （傳出） 端點。 預設值， [\<路由 >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)行為會建立並附加新[ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md)行為`processMessages`設`true`每個用戶端端點。 如果路由服務無法辨識您的通訊協定，或者您想要覆寫預設的處理行為，可以停用整個路由服務的 SOAP 處理，或者只停用特定端點的 SOAP 處理。  若要停用整個路由服務在所有端點上的 SOAP 處理，請設定`soapProcessing`的屬性[\<路由 >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)行為`false`。 若要關閉特定端點的 SOAP 處理，請使用這個行為，並將其 `processMessages` 屬性設定為 `false`，然後將這個屬性附加至某個端點 (您不希望預設處理程式碼在此端點上執行)。  當[\<路由 >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)行為設定路由服務時，它會略過重複套用端點行為，因為已經存在。
