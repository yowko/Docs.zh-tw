---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: aed65311d2b36a5dc764511de04e34c4bfb69d7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59978168"
---
# <a name="mtommessageencodingbindingelement"></a>MtomMessageEncodingBindingElement
MtomMessageEncodingBindingElement  
  
## <a name="syntax"></a>語法  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>方法  
 MtomMessageEncodingBindingElement 類別並未定義任何方法。  
  
## <a name="properties"></a>屬性  
 MtomMessageEncodingBindingElement 類別具有下列屬性：  
  
### <a name="encoding"></a>編碼  
 資料型別：字串  
  
 存取類型：唯讀  
  
 要在繫結上發出訊息時使用的字元集編碼方式。  
  
### <a name="maxreadpoolsize"></a>MaxReadPoolSize  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 定義可同時讀取之訊息數目 (在不配置新讀取器的情況下) 的整數。  
  
### <a name="maxwritepoolsize"></a>MaxWritePoolSize  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 定義可同時傳送之訊息數目 (在不配置新寫入器的情況下) 的整數。  
  
### <a name="readerquotas"></a>ReaderQuotas  
 資料類型：XmlDictionaryReaderQuotas  
  
 存取類型：唯讀  
  
 讀取器的配額。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
