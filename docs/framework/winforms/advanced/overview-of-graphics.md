---
title: "圖形概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "圖形, 關於圖形"
  - "圖形, 使用 Managed 介面"
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 圖形概觀
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 是構成 Microsoft Windows 作業系統之子系統的應用程式開發介面 \(API\)。[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 會負責顯示螢幕和印表機上的資訊。  正如其名， [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 是 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 的後置項，該繪圖裝置介面包含在舊版 Windows 中。  
  
## Managed 類別介面  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 應用程式開發介面透過一組部署為 Managed 程式碼的類別公開。  這組類別稱為 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 的  *Managed 類別介面*。  下列命名空間組成 Managed 類別介面：  
  
-   <xref:System.Drawing>  
  
-   <xref:System.Drawing.Drawing2D>  
  
-   <xref:System.Drawing.Imaging>  
  
-   <xref:System.Drawing.Text>  
  
-   <xref:System.Drawing.Printing>  
  
 圖形裝置介面，例如 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，您可以在螢幕或印表機上顯示資訊，而不須關心特定顯示裝置的詳細資料。  程式設計師會呼叫 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 類別所提供的方法。這些方法接著會適當地呼叫特定裝置驅動程式。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 會從圖形硬體隔離應用程式。隔離會讓程式設計人員能夠建立與裝置無關的應用程式。  
  
## 請參閱  
 [圖形概觀](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)