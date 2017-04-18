---
title: "如何：選擇不自動升級檔案對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "OpenFileDialog [Windows Form]，選擇不自動升級"
  - "檔案對話方塊 [Windows Form]，選擇不自動升級"
  - "Windows Vista 檔案對話方塊方塊中，選擇不自動升級"
  - "SaveFileDialog [Windows Form]，選擇不自動升級"
  - "AutoUpgradeEnabled 屬性"
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：選擇不自動升級檔案對話方塊
當<xref:System.Windows.Forms.OpenFileDialog>和<xref:System.Windows.Forms.SaveFileDialog>應用程式中使用類別，其外觀和行為取決於 Windows 執行應用程式的版本。 當應用程式在建立[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]或前面會顯示在[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)]， <xref:System.Windows.Forms.OpenFileDialog>和<xref:System.Windows.Forms.SaveFileDialog>會自動顯示與[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)]外觀和行為。 從[!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)]，您可以選擇不自動升級，以顯示<xref:System.Windows.Forms.OpenFileDialog>和<xref:System.Windows.Forms.SaveFileDialog>與[!INCLUDE[winxp](../../../../includes/winxp-md.md)]-樣式外觀和行為。  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>若要升級檔案對話方塊自動選擇退出  
  
1.  設定<xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A>屬性<xref:System.Windows.Forms.OpenFileDialog>或<xref:System.Windows.Forms.SaveFileDialog>至`false`對話方塊顯示之前。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.FileDialog>