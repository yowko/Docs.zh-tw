---
title: XAML 啟用
ms.date: 03/30/2017
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
ms.openlocfilehash: 8621b0ea7b390c81e76ac7eeedb0b547b44320d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517708"
---
# <a name="xaml-activation"></a>XAML 啟用
這個範例示範如何在 IIS 中裝載宣告式工作流程。 此範例是有一個作業的基本工作流程，名為 `EchoService`。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 （下載頁面） 以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 XAMLActivation.sln 方案。  
  
2.  按下建置此方案**F5**。  
  
3.  執行 WcfTestClient.exe。 從命令提示字元中輸入下列命令：  
  
    1.  cd %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE  
  
    2.  執行 WcfTestClient.exe。  
  
4.  在 WcfTestClient.exe 設定服務的位址，按下 CTRL + SHIFT + A，並設定服務位址為http://localhost:56133/Service.xamlx。  
  
5.  執行 Echo 作業以測試服務。  
  
6.  在命令提示字元中，以系統管理員權限使用 DeployToIIS.Bat，以在 IIS 中部署服務。  
  
7.  在用戶端的服務位址更新http://localhost/XAMLActivation/Service.xamlx和測試使用 WcfTestClient.exe 再次服務。
