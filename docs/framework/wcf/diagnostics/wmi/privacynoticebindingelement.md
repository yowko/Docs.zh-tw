---
title: PrivacyNoticeBindingElement
ms.date: 03/30/2017
ms.assetid: 0cf110b1-e25b-4d67-986b-10cb04dc4826
ms.openlocfilehash: 04c65d0aa589d99766b4ffc8f1550036d2880718
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976374"
---
# <a name="privacynoticebindingelement"></a>PrivacyNoticeBindingElement
PrivacyNoticeBindingElement  
  
## <a name="syntax"></a>語法  
  
```csharp
class PrivacyNoticeBindingElement : BindingElement  
{  
  sint32 PrivacyNoticeVersion;  
  string Url;  
};  
```  
  
## <a name="methods"></a>方法  
 PrivacyNoticeBindingElement 類別並未定義任何方法。  
  
## <a name="properties"></a>屬性  
 PrivacyNoticeBindingElement 類別具有下列屬性：  
  
### <a name="privacynoticeversion"></a>PrivacyNoticeVersion  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 隱私權注意事項的版本。  
  
### <a name="url"></a>URL  
 資料型別：字串  
  
 存取類型：唯讀  
  
 隱私權注意事項所在的 URL。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
