---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: f24865fb0affa7b4516a14fc05b905995826e82e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597667"
---
# <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas
XmlDictionaryReaderQuotas  
  
## <a name="syntax"></a>語法  
  
```csharp
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a>方法  
 XmlDictionaryReaderQuotas 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 XmlDictionaryReaderQuotas 類別有下列屬性：  
  
### <a name="maxarraylength"></a>MaxArrayLength  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 允許的陣列長度上限。  
  
### <a name="maxbytesperread"></a>MaxBytesPerRead  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 允許每個讀取動作傳回的位元組上限。  
  
### <a name="maxdepth"></a>MaxDepth  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 每個讀取動作的巢狀節點深度上限。  
  
### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 資料表名稱允許的字元數目上限。  
  
### <a name="maxstringcontentlength"></a>MaxStringContentLength  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 XML 項目內容允許的字元數目上限。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Xml.XmlDictionaryReaderQuotas>
- <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
