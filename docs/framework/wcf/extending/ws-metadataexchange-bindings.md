---
title: "WS-MetadataExchange 繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d305f3bf34b3b14da566fa792552e24e695ef33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ws-metadataexchange-bindings"></a>WS-MetadataExchange 繫結
本主題會說明如何為各種傳輸建構預設中繼資料交換繫結。  
  
## <a name="the-default-bindings"></a>預設繫結  
  
|預設繫結名稱|繫結的建構方式|  
|--------------------------|------------------------------------|  
|MexHttpBinding|已停用傳輸層級安全性的 <xref:System.ServiceModel.WSHttpBinding>。|  
|MexHttpsBinding|支援傳輸層級安全性的 <xref:System.ServiceModel.WSHttpBinding>。|  
|MexNamedPipeBinding|具有使用預設值之 <xref:System.ServiceModel.Channels.CustomBinding><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>的 。|  
|MexTcpBinding|具有使用預設值之 <xref:System.ServiceModel.Channels.CustomBinding> 的 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>。|
