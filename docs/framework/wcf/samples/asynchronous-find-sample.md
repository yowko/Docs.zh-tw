---
title: "非同步尋找範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b0b21e9d75c0145c9bd3fa5edf13913cf43f461
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="asynchronous-find-sample"></a>非同步尋找範例
此範例示範如何從用戶端應用程式使用非同步尋找作業。  
  
## <a name="sample-details"></a>範例詳細資料  
 遵循此設計模式的優點在於，用戶端會以非同步方式，收到當做尋找要求結果搜尋之端點的通知。 若要了解其運作方式，請開啟 Client.cs 檔案。 請注意，<xref:System.ServiceModel.Discovery.DiscoveryClient> 物件有兩個連接至其事件處理常式的委派。 其中一個委派會在引發 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> 事件時呼叫，而另一個委派，則會在每次引發 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> 事件時呼叫。 此範例示範如何在應用程式中使用此模式。  
  
> [!NOTE]
>  這個範例使用 HTTP 端點，若要執行，則必須加入正確的 URL ACL。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][設定 HTTP 和 HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)。 以更高的權限執行下列命令應該就能加入適當的 ACL。 如果命令未正確執行，您可能要將 domain 和 username 替換成下列引數。 `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 AsyncFind.sln。  
  
2.  按下 CTRL+SHIFT+B 以建置方案。  
  
3.  開啟 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元並巡覽至 \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug 或 \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug 目錄，然後執行 Service.exe。  
  
4.  服務啟動後，巡覽至 \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug 或 WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug 目錄，然後執行 Client.exe。  
  
5.  請注意，用戶端可以尋找與呼叫服務。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a>請參閱
