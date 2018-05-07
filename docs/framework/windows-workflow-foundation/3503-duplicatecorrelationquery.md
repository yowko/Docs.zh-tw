---
title: 3503 - DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: 37a689b30b0bcab9124472deb98627afbe30dfee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="3503---duplicatecorrelationquery"></a>3503 - DuplicateCorrelationQuery
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|ID|3503|  
|關鍵字|WFServices|  
|層級|警告|  
|通道|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>描述  
 表示發現重複的 CorrelationQuery。 在計算相互關聯時，不會使用重複的查詢。  
  
## <a name="message"></a>訊息  
 發現 Where='%1' 的重複 CorrelationQuery。 計算相互關聯時不會使用這個重複的查詢。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|位置|xs:string|相互關聯查詢的 Where 部分。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
