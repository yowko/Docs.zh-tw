---
title: CustomBindingElement
ms.date: 03/30/2017
ms.assetid: df959dc5-1aef-4338-a123-6ff3e7bc37af
ms.openlocfilehash: d7c8a46032aff4d5d2b3c4be8e887953ec1d2c11
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270728"
---
# <a name="custombindingelement"></a>CustomBindingElement

CustomBindingElement  
  
## <a name="syntax"></a>Syntax  
  
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
  
### <a name="name"></a>Name  

 資料類型：字串  
  
 存取類型：唯讀  
  
 包含繫結之組態名稱的字串。 這個值是使用者定義的字串，它會充當自訂繫結的識別字串。  
  
## <a name="requirements"></a>規格需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.CustomBinding>
