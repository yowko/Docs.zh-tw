---
title: 將 .NET 遠端處理應用程式移轉到 WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 2cfaebd064d10e5b331412d177929ecb20117a07
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248210"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>將 .NET 遠端處理應用程式移轉到 WCF

**本主題是針對與現有應用程式的回溯相容性而保留的舊版技術所特有，不建議用於新的開發。現在應該使用 WCF 開發分散式應用程式。**  
  
 有兩種方式可利用 WCF 與現有的 .NET 遠端應用程式：整合和遷移。 整合可讓您讓 .NET 遠端處理2.0 和 WCF 並存執行，讓您同時公開兩種技術的相同商務物件，而不需要修改現有的 .NET Remoting 2.0 程式碼。 您需要在 .NET Framework 2.0 或更高版本上執行整合。 如果您想要利用 WCF 功能，而不需要與遠端2.0 系統的網路相容性，您可以將整個服務遷移至 WCF。 從 .NET 遠端處理2.0 遷移至 WCF 需要變更遠端物件的介面及其設定。 這兩個主題都涵蓋于 [從遠端處理至 Windows Communication Foundation](/previous-versions/aa730857(v=vs.80))。  
  
## <a name="see-also"></a>另請參閱

- [概觀說明](../conceptual-overview.md)
