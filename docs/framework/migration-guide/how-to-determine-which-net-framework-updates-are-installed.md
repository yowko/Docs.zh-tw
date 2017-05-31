---
title: "如何：判斷安裝的 .NET Framework 更新 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
caps.latest.revision: 6
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: dc1c456c71efb3cc6e60a8fdc77384e65975f110
ms.openlocfilehash: 6237bdaf1d12743bee71633acf8cef69c21b414e
ms.contentlocale: zh-tw
ms.lasthandoff: 05/15/2017

---
# <a name="how-to-determine-which-net-framework-updates-are-installed"></a>如何：判斷安裝的 .NET Framework 更新
電腦上所安裝之每一版 .NET Framework 已安裝的更新都會列在 Windows 登錄中。 您可以使用登錄編輯程式 (regedit.exe) 檢視這項資訊。  
  
 在登錄編輯程式中，.NET Framework 版本和每一版已安裝的更新會儲存在不同的子機碼中。 如需偵測已安裝之版本號碼的相關資訊，請參閱[如何：判斷安裝的 .NET Framework 版本](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)。 如需安裝 .NET Framework 的資訊，請參閱[安裝指南](../../../docs/framework/install/guide-for-developers.md)。  
  
### <a name="to-find-installed-updates"></a>尋找已安裝的更新  
  
1.  開啟 **regedit.exe** 程式。 在 Windows 8 (含) 以上版本中，開啟 [開始] 畫面，然後輸入名稱。 在舊版 Windows 中，於 [開始] 功能表上選擇 [執行]，然後在 [開啟] 方塊中輸入 **regedit.exe**。  
  
     您必須具有系統管理認證才能執行 regedit.exe。  
  
2.  在 [登錄編輯程式] 中，開啟下列子機碼：  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates  
  
     已安裝的更新會列於子機碼下，這些子機碼可識別套用更新的 .NET Framework 版本。 每個更新都是透過知識庫 (KB) 號碼加以識別。  
  
## <a name="example"></a>範例  
 下列程式碼以程式設計方式判斷電腦上所安裝的 .NET Framework 更新。 您必須具有系統管理認證才能執行這個範例。  
  
 [!code-csharp[ListUpdates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs#1)] [!code-vb[ListUpdates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb#1)]  
  
 這個範例產生的輸出類似下面所述：  
  
```  
  
Microsoft .NET Framework 3.5 SP1  
  KB953595  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB953595)  
  SP1  
    KB2657424  Security Update for Microsoft .NET Framework 3.5 SP1 (KB2657424)  
    KB958484  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB958484)  
    KB963707  Update for Microsoft .NET Framework 3.5 SP1 (KB963707)  
Microsoft .NET Framework 4 Client Profile  
  KB2160841  Security Update for Microsoft .NET Framework 4 Client Profile (KB2160841)  
  KB2446708  Security Update for Microsoft .NET Framework 4 Client Profile (KB2446708)  
  KB2468871  Update for Microsoft .NET Framework 4 Client Profile (KB2468871)  
  KB2478663  Security Update for Microsoft .NET Framework 4 Client Profile (KB2478663)  
  KB2518870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2518870)  
  KB2533523  Update for Microsoft .NET Framework 4 Client Profile (KB2533523)  
  KB2539636  Security Update for Microsoft .NET Framework 4 Client Profile (KB2539636)  
  KB2572078  Security Update for Microsoft .NET Framework 4 Client Profile (KB2572078)  
  KB2633870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2633870)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Client Profile (KB2656351)  
Microsoft .NET Framework 4 Extended  
  KB2416472  Security Update for Microsoft .NET Framework 4 Extended (KB2416472)  
  KB2468871  Update for Microsoft .NET Framework 4 Extended (KB2468871)  
  KB2487367  Security Update for Microsoft .NET Framework 4 Extended (KB2487367)  
  KB2533523  Update for Microsoft .NET Framework 4 Extended (KB2533523)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Extended (KB2656351)  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [如何：判斷安裝的 .NET Framework 版本](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)   
 [安裝指南](../../../docs/framework/install/guide-for-developers.md)   
 [版本和相依性](../../../docs/framework/migration-guide/versions-and-dependencies.md)

