---
title: CustomBindingElement
ms.date: 03/30/2017
ms.assetid: df959dc5-1aef-4338-a123-6ff3e7bc37af
ms.openlocfilehash: 23c8e7ca87002a6ee0c6e6a7aba649e00acbdc4d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681673"
---
# <a name="custombindingelement"></a>CustomBindingElement
CustomBindingElement  
  
## <a name="syntax"></a>語法  
  
```csharp
class CustomBindingElement : BindingElement  
{  
  string Name;  
};  
```  
  
## <a name="methods"></a>方法  
 CustomBindingElement 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 CustomBindingElement 類別具有下列屬性：  
  
### <a name="name"></a>名稱  
 資料型別：字串  
  
 存取類型：唯讀  
  
 包含繫結之組態名稱的字串。 這個值是使用者定義的字串，它會充當自訂繫結的識別字串。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.Channels.CustomBinding>
