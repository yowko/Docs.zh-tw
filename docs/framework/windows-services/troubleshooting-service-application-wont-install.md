---
title: "疑難排解： 服務應用程式成交 &#39; t 安裝"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 82eb870761a7865385631cd9961ce99e0b0d3502
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="troubleshooting-service-application-won39t-install"></a>疑難排解： 服務應用程式成交 &#39; t 安裝
如果您的服務應用程式將無法正確安裝，請檢查並確定<xref:System.ServiceProcess.ServiceBase.ServiceName%2A>該服務的安裝程式中所顯示的服務類別的屬性設定為相同的值。 值必須是相同的兩個執行個體，為了讓您的服務已正確安裝。  
  
> [!NOTE]
>  您也可以查看安裝記錄檔以取得安裝程序的回饋意見。  
  
 您也應該檢查以判斷您是否有另一個服務，已安裝相同的名稱。 服務名稱必須是唯一的才能成功安裝。  
  
## <a name="see-also"></a>另請參閱  
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
