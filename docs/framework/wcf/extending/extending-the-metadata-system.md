---
title: "擴充中繼資料系統"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aca7a7aba7ef4a40100e9858561d197916b71544
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-metadata-system"></a>擴充中繼資料系統
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中繼資料系統是一個由類別和介面組成的群組，代表實作服務應用程式所需的中繼資料。 修改或擴充類別，或是實作和設定介面，即可匯出和匯入自訂中繼資料 (例如 Web 服務描述語言 (WSDL) 擴充功能或自訂 WS-PolicyAttachments 判斷提示)。  
  
## <a name="in-this-section"></a>本節內容  
 [匯出 WCF 延伸模組的自訂中繼資料](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 描述如何實作和使用 <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> 介面，將自訂原則判斷提示嵌入 WSDL 文件中。  
  
 [匯入 WCF 延伸模組的自訂中繼資料](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)  
 描述如何實作和使用 <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> 介面，讀取和回應 WSDL 文件中的自訂原則判斷提示。  
  
 [發行與擷取自訂繫結上的中繼資料](../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 描述如何透過自訂繫結交換中繼資料。
