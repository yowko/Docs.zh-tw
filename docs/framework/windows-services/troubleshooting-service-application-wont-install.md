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
ms.openlocfilehash: d04a0ddcef9ff7c31abd422f7f9fba34e804d2b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935419"
---
# <a name="troubleshooting-service-application-wont-install"></a>疑難排解：無法安裝服務應用程式
如果您的服務應用程式無法正確安裝，請檢查以確定會將服務類別的 <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> 屬性設定為與該服務安裝程式中所示相同的值。 此值在這兩個執行個體中必須一樣，才能正確安裝您的服務。  
  
> [!NOTE]
> 您也可以查看安裝記錄以取得關於安裝程序的回饋意見。  
  
 您也應該檢查以判斷是否已經安裝另一個具有相同名稱的服務。 服務名稱必須是唯一的，才能成功安裝。  
  
## <a name="see-also"></a>另請參閱

- [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
