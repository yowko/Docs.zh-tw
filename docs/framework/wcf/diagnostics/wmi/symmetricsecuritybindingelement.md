---
title: SymmetricSecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7960ae9972490f2363b0f6f9942e947677c7d299
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="symmetricsecuritybindingelement"></a>SymmetricSecurityBindingElement
SymmetricSecurityBindingElement  
  
## <a name="syntax"></a>語法  
  
```  
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
 資料型別：字串  
  
 存取類型：唯讀  
  
 這個繫結的訊息加密和簽章順序。  
  
### <a name="requiresignatureconfirmation"></a>RequireSignatureConfirmation  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 繫結是否需要簽章確認。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
