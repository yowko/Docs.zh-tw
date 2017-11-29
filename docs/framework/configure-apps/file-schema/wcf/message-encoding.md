---
title: "訊息編碼"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ec7a85e95de9608d7a7daff11d70c9da3ff82989
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="message-encoding"></a>訊息編碼
編碼是將一組 Unicode 字元轉換成位元組序列的處理程序。 解碼則是相反的處理序。 Windows Communication Foundation (WCF) 包含 SOAP 訊息的三種編碼類型：文字、二進位和訊息傳輸最佳化機制 (MTOM)。  
  
 `binaryMessageEncoding` 組態區段會指定用於二進位 XML 訊息的字元編碼和訊息版本處理。 二進位訊息編碼器會以二進位編碼網路上的 Windows Communication Foundation (WCF) 訊息。 雖然這個編碼會讓訊息傳輸速度非常快，但是會失去以 WS-* 標準為基礎的互通性 (Interoperability)。  
  
 `mtomMessageEncoding` 組態區段會指定字元編碼方式和訊息版本處理，用於使用訊息傳輸最佳化機制 (MTOM) 編碼方式的訊息。 (MTOM) 是在 Windows Communication Foundation (WCF) 訊息中傳輸二進位資料的有效技術。 MTOM 編碼器會嘗試在效率和互通性之間保持平衡。 MTOM 編碼方式會以文字格式傳輸大部分的 XML，但是在傳輸大型區塊的二進位資料時，會依照原狀來傳送 (不轉換成文字)，好讓這些資料最佳化。  
  
 `textMessageEncoding` 組態區段會指定文字編碼器，以用於建立網路上的文字訊息。 此編碼器產生的訊息適合 WS-* 型的互通性。 Web 服務或 Web 服務用戶端通常可以了解文字 XML。 不過，若要針對 XML 訊息進行編碼，將大型二進位資料區塊當做文字傳輸是效率最差的方法。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [選擇訊息編碼器](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
