---
title: 中繼資料存放區可程式性
ms.date: 03/30/2017
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
ms.openlocfilehash: 9f30fcdac131b8749a4d165875b9bbb584542843
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088200"
---
# <a name="metadata-store-programmability"></a>中繼資料存放區可程式性
中繼資料存放區是讓任意中繼資料 (CLR 屬性形式) 與執行階段類型產生關聯的 [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] 功能。 這啟用執行階段元件與其設計階段對應項目之間的鬆散結合，也提供變更設計階段元件但不影響執行階段的能力。 此範例示範如何透過將屬性套用至我們沒有控制權的執行階段類型，對中繼資料存放區撰寫程式。 一般用語是主控應用程式註冊一組類型的中繼資料。  
  
 在輸出中，您會注意到額外、非預期的屬性 <xref:System.Runtime.InteropServices.GuidAttribute>。 這是在使用中繼資料 API 時加入的，對範例執行沒有影響。  
  
 這個範例會示範下列情況：  
  
## <a name="demonstrates"></a>示範  
  
-   使用中繼資料存放區 API 的屬性插入。  
  
-   使用回呼機制延後中繼資料註冊。  
  
## <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 ProgrammingMetadataStore.sln 方案檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按 F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`