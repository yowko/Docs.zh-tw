---
title: PeerCustomResolverBindingElement
ms.date: 03/30/2017
ms.assetid: 9ccc2770-a20e-4dff-9970-f56ad8aec2b5
ms.openlocfilehash: 62e52a1ebec8a55b51d3c918971c420fe45fdaa1
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50037859"
---
# <a name="peercustomresolverbindingelement"></a>PeerCustomResolverBindingElement
PeerCustomResolverBindingElement  
  
## <a name="syntax"></a>語法  
```csharp
class PeerCustomResolverBindingElement : PeerResolverBindingElement
{  
    string Address;
    string Binding;
};
```  
  
## <a name="methods"></a>方法  
 PeerCustomResolverBindingElement 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 PeerCustomResolverBindingElement 類別有下列屬性：  
  
### <a name="address"></a>地址  
 資料型別：字串  
  
 存取類型：唯讀  
  
 對等自訂解析程式的位址。  
  
### <a name="binding"></a>繫結  
 資料型別：字串  
  
 存取類型：唯讀  
  
 繫結的組態名稱。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.PeerCustomResolverBindingElement>
