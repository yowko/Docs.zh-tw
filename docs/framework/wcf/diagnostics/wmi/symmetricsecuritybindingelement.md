---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: c618b5b41790b04a84b4c50fe47baa2c0cb05ab2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274097"
---
# <a name="symmetricsecuritybindingelement"></a>SymmetricSecurityBindingElement

SymmetricSecurityBindingElement  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>方法  

 SymmetricSecurityBindingElement 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  

 SymmetricSecurityBindingElement 類別具有下列屬性：  
  
### <a name="messageprotectionorder"></a>MessageProtectionOrder  

 資料類型：字串  
  
 存取類型：唯讀  
  
 這個繫結的訊息加密和簽章順序。  
  
### <a name="requiresignatureconfirmation"></a>RequireSignatureConfirmation  

 資料型別：布林值  
  
 存取類型：唯讀  
  
 繫結是否需要簽章確認。  
  
## <a name="requirements"></a>規格需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
