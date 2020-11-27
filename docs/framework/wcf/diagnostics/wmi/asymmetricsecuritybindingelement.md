---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 00485ff80a0064e700d99203de3aa581d3761f30
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255724"
---
# <a name="asymmetricsecuritybindingelement"></a>AsymmetricSecurityBindingElement

AsymmetricSecurityBindingElement  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>方法  

 AsymmetricSecurityBindingElement 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  

 AsymmetricSecurityBindingElement 類別具有下列屬性：  
  
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

- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
