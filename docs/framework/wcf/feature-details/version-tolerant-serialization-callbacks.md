---
title: 版本相容序列化回呼
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OnDeserializedAttribute [WCF]
- OnDeserializingAttribute [WCF]
- OnSerializingAttribute [WCF]
- serialization [WCF], setting default values
- OnSerializedAttribute [WCF]
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
ms.openlocfilehash: 84e38451f10acc341642c0bf0923cc73b79d771f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="version-tolerant-serialization-callbacks"></a>版本相容序列化回呼
資料合約程式設計模型完整支援 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 和 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 類別所支援的版本相容序列化回呼方法。  
  
## <a name="version-tolerant-attributes"></a>版本相容的屬性  
 回呼屬性有四個。 每個屬性都可以套用至序列化/還原序列化引擎在不同時間呼叫的方法。 下表說明何時使用各個屬性。  
  
|屬性|呼叫對應方法的時機|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|在序列化型別之前呼叫。|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|在序列化型別之後呼叫。|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|在還原序列化型別之前呼叫。|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|在還原序列化型別之後呼叫。|  
  
 這些方法必須接受 <xref:System.Runtime.Serialization.StreamingContext> 參數。  
  
 這些方法主要是搭配版本處理或初始化使用。 在還原序列化期間，不會呼叫建構函式。 因此，如果資料成員的資料在傳入資料流中遺失 (例如，當資料來自遺失某些資料成員的舊版型別時)，則這些資料成員可能無法正確地初始化 (做為預設值)。 如果要修正這個問題，請使用以 <xref:System.Runtime.Serialization.OnDeserializingAttribute> 標示的回呼方法，如下例中所示。  
  
 每種型別只有一個方法可以標上前述各個回呼屬性。  
  
### <a name="example"></a>範例  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.Serialization.OnSerializingAttribute>  
 <xref:System.Runtime.Serialization.OnSerializedAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
 <xref:System.Runtime.Serialization.StreamingContext>  
 [版本相容序列化](../../../../docs/standard/serialization/version-tolerant-serialization.md)
