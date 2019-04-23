---
title: 疑難排解：無法安裝服務應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
author: ghogen
ms.openlocfilehash: f75a2f33ecde408d2d8e2f2343197ba56c4b8c21
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143815"
---
# <a name="troubleshooting-service-application-wont-install"></a><span data-ttu-id="eba7a-102">疑難排解：無法安裝服務應用程式</span><span class="sxs-lookup"><span data-stu-id="eba7a-102">Troubleshooting: Service Application Won't Install</span></span>
<span data-ttu-id="eba7a-103">如果您的服務應用程式無法正確安裝，請檢查以確定會將服務類別的 <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> 屬性設定為與該服務安裝程式中所示相同的值。</span><span class="sxs-lookup"><span data-stu-id="eba7a-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="eba7a-104">此值在這兩個執行個體中必須一樣，才能正確安裝您的服務。</span><span class="sxs-lookup"><span data-stu-id="eba7a-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eba7a-105">您也可以查看安裝記錄以取得關於安裝程序的回饋意見。</span><span class="sxs-lookup"><span data-stu-id="eba7a-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="eba7a-106">您也應該檢查以判斷是否已經安裝另一個具有相同名稱的服務。</span><span class="sxs-lookup"><span data-stu-id="eba7a-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="eba7a-107">服務名稱必須是唯一的，才能成功安裝。</span><span class="sxs-lookup"><span data-stu-id="eba7a-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eba7a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eba7a-108">See also</span></span>

- [<span data-ttu-id="eba7a-109">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="eba7a-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
