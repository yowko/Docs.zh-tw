---
title: "XAML 啟用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ac691e3d24e3526b43a6818fbe6bbb33a3375a7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="xaml-activation"></a>XAML 啟用
這個範例示範如何在 IIS 中裝載宣告式工作流程。 此範例是有一個作業的基本工作流程，名為 `EchoService`。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 (下載頁面) 以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 XAMLActivation.sln 方案。  
  
2.  按下建置此方案**F5**。  
  
3.  執行 WcfTestClient.exe。 從命令提示字元中輸入下列命令：  
  
    1.  cd %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE  
  
    2.  執行 WcfTestClient.exe。  
  
4.  在 WcfTestClient.exe 設定服務位址，方式是按 CTRL+SHIFT+A，將服務位址設為 http://localhost:56133/Service.xamlx。  
  
5.  執行 Echo 作業以測試服務。  
  
6.  在命令提示字元中，以系統管理員權限使用 DeployToIIS.Bat，以在 IIS 中部署服務。  
  
7.  將用戶端上的服務位址更新為 http://localhost/XAMLActivation/Service.xamlx，並且使用 WcfTestClient.exe 再次測試服務。
