---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 334bab97a04ed464dce6944692b04a9ed1295296
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613816"
---
# <a name="mustunderstandbehavior"></a>MustUnderstandBehavior
MustUnderstandBehavior  
  
## <a name="syntax"></a>語法  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>方法  
 MustUnderstandBehavior 類別並未定義任何方法。  
  
## <a name="properties"></a>屬性  
 MustUnderstandBehavior 類別具有下列屬性：  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 當 `true``MustUnderstand`時，所有具有  屬性且未處理的 SOAP 標頭，會導致該行為擲出例外狀況。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.Description.MustUnderstandBehavior>
