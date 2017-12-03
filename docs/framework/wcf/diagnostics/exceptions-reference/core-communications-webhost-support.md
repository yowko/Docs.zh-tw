---
title: "核心通訊：Webhost 支援"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 034c501f-96f9-4ef7-9602-3ac21788fd3e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 707b97c49d6a6f5262719e91f8cb38fe7da53601
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="core-communications-webhost-support"></a>核心通訊：Webhost 支援
本主題會列出由 Webhost 支援產生的所有例外狀況。  
  
## <a name="exception-list"></a>例外狀況清單  
  
|資源程式碼|資源字串|  
|-------------------|---------------------|  
|Hosting_CompatibilityServiceNotHosted|這個服務必須相容於 ASP.NET。 而且它必須裝載於 IIS。 請將此服務裝載於 IIS 並且啟用 Web.config 中的 ASP.NET 相容性，或是將 AspNetCompatibilityRequirementsAttribute.AspNetCompatibilityRequirementsMode 屬性設定成必要項以外的值。|  
|Hosting_ListenerNotFoundForActivationInRecycling|沒有任何通道正在主動接聽指定的位址。 如果應用程式正在回收處理，服務就會關閉。|  
|Hosting_NonHTTPInCompatibilityMode|在 ASP.NET 相容性下唯一支援的通訊協定為 HTTP 和 HTTPS。 請移除指定的端點或停用應用程式的 ASP.NET 相容性。|  
|Hosting_ProcessNotExecutingUnderHostedContext|無法在目前的裝載環境中叫用指定的裝載處理序。 這個 API 要求呼叫應用程式必須是裝載於網際網路資訊服務或 Windows Process Activation Service。|  
|Hosting_ServiceCompatibilityRequire|無法啟動這個服務，因為它需要 ASP.NET 相容性。 沒有啟用這個應用程式的 ASP.NET 相容性。 請啟用 Web.config 中的 ASP.NET 相容性或設定 AspNetCompatibilityRequirementsAttribute.AspNetCompatibility。|
