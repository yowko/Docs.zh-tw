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
# <a name="troubleshooting-service-application-won39t-install"></a><span data-ttu-id="850be-102">疑難排解： 服務應用程式成交 &#39; t 安裝</span><span class="sxs-lookup"><span data-stu-id="850be-102">Troubleshooting: Service Application Won&#39;t Install</span></span>
<span data-ttu-id="850be-103">如果您的服務應用程式將無法正確安裝，請檢查並確定<xref:System.ServiceProcess.ServiceBase.ServiceName%2A>該服務的安裝程式中所顯示的服務類別的屬性設定為相同的值。</span><span class="sxs-lookup"><span data-stu-id="850be-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="850be-104">值必須是相同的兩個執行個體，為了讓您的服務已正確安裝。</span><span class="sxs-lookup"><span data-stu-id="850be-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="850be-105">您也可以查看安裝記錄檔以取得安裝程序的回饋意見。</span><span class="sxs-lookup"><span data-stu-id="850be-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="850be-106">您也應該檢查以判斷您是否有另一個服務，已安裝相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="850be-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="850be-107">服務名稱必須是唯一的才能成功安裝。</span><span class="sxs-lookup"><span data-stu-id="850be-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="850be-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="850be-108">See Also</span></span>  
 [<span data-ttu-id="850be-109">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="850be-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
