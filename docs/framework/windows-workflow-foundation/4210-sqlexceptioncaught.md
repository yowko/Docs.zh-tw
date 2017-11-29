---
title: 4210 - SqlExceptionCaught
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a3fb3c780b80172db8770e717f517b97608fcb7c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="4210---sqlexceptioncaught"></a>4210 - SqlExceptionCaught
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|ID|4210|  
|關鍵字|WFInstanceStore|  
|層級|警告|  
|通道|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  
 表示已攔截到 SQL 例外狀況。  
  
## <a name="message"></a>訊息  
 攔截到 SQL 例外狀況編號 %1 訊息 %2。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|ErrorNumber|xs:string|SQL 錯誤代碼。|  
|ExceptionMessage|xs:string|SQL 例外狀況的訊息。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
