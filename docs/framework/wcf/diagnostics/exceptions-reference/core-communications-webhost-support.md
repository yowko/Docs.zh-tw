---
title: 核心通訊：Webhost 支援
ms.date: 03/30/2017
ms.assetid: 034c501f-96f9-4ef7-9602-3ac21788fd3e
ms.openlocfilehash: 8ee107ffcb9fab629541ce004d1c587fcad652c8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503454"
---
# <a name="core-communications-webhost-support"></a>核心通訊：Webhost 支援

本主題會列出由 Webhost 支援產生的所有例外狀況。

## <a name="exception-list"></a>例外狀況清單

|資源程式碼|資源字串|
|-------------------|---------------------|
|Hosting_CompatibilityServiceNotHosted|這個服務必須相容於 ASP.NET。 而且它必須裝載於 IIS。 請將此服務裝載於 IIS 並且啟用 Web.config 中的 ASP.NET 相容性，或是將 AspNetCompatibilityRequirementsAttribute.AspNetCompatibilityRequirementsMode 屬性設定成必要項以外的值。|
|Hosting_ListenerNotFoundForActivationInRecycling|沒有任何通道正在主動接聽指定的位址。 如果應用程式正在回收處理，服務就會關閉。|
|Hosting_NonHTTPInCompatibilityMode|在 ASP.NET 相容性下唯一支援的通訊協定為 HTTP 和 HTTPS。 請移除指定的端點或停用應用程式的 ASP.NET 相容性。|
|Hosting_ProcessNotExecutingUnderHostedContext|指定的裝載處理序無法在目前的主控環境內叫用。 這個 API 要求呼叫應用程式必須是裝載於網際網路資訊服務或 Windows Process Activation Service。|
|Hosting_ServiceCompatibilityRequire|無法啟動這個服務，因為它需要 ASP.NET 相容性。 沒有啟用這個應用程式的 ASP.NET 相容性。 請啟用 Web.config 中的 ASP.NET 相容性或設定 AspNetCompatibilityRequirementsAttribute.AspNetCompatibility。|
