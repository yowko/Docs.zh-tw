---
title: "在 Windows Form 上裝載 ActiveX 控制項的考慮因素 | Microsoft Docs"
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
  - "ActiveX 控制項 [Windows Form], 加入"
  - "ActiveX 控制項 [Windows Form], 裝載"
  - "Windows Form 控制項, ActiveX 控制項"
  - "Windows Form, ActiveX 控制項"
  - "Windows Form, 裝載 ActiveX 控制項"
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 在 Windows Form 上裝載 ActiveX 控制項的考慮因素
雖然 Windows Form 是最佳化來裝載 \(Host\) Windows Form 控制項，但您還是可使用 ActiveX 控制項。  在規劃使用 ActiveX 控制項的應用程式時，請務必考慮下列事項：  
  
-   **安全性**：Common Language Runtime 已在程式碼存取的安全性方面加強。  具有 Windows Form 的應用程式可在完全受信任的環境下正常運作，而且也可在非完全信任的環境下存取大部分的功能。  Windows Form 控制項可以輕易地裝載於瀏覽器中。  但是，Windows Form 上的 ActiveX 控制項無法享有這些安全性增強的好處。  執行 ActiveX 控制項需要 Unmanaged 程式碼使用權限，您可使用 <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=fullName> 屬性加以設定。  如需安全性和 Unmanaged  程式碼使用權限，請參閱 [SecurityPermissionAttribute 類別](frlrfSystemSecurityPermissionsSecurityPermissionAttributeClassTopic)。  
  
-   **整體擁有成本 \(TCO\)**：任何加入至 Windows Form 的 ActiveX 控制項都會與該 Windows Form 一起部署，這麼做會明顯地增加已建立檔案的大小。  此外，在 Windows Form 上使用 ActiveX 控制項必須寫入登錄。  對使用者的電腦而言，這比 Windows Form 控制項更具侵入性，因為 Windows Form 控制項不需要這麼做。  
  
    > [!NOTE]
    >  使用 ActiveX 控制項需要 COM Interop 包裝函式。  如需詳細資訊，請參閱 [Visual Basic 和 Visual C\# 中的 COM 互通性](../Topic/COM%20Interoperability%20in%20.NET%20Framework%20Applications%20\(Visual%20Basic\).md)。  
  
    > [!NOTE]
    >  如果 ActiveX 控制項成員的名稱與 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中定義的名稱相符，則 ActiveX 控制項匯入工具會在建立 <xref:System.Windows.Forms.AxHost> 衍生類別 \(Derived Class\) 時，在成員名稱前加上 **Ctl** 前置詞。  例如，如果 ActiveX 控制項有名為 **Layout** 的成員，它在 AxHost 衍生類別中會重新命名為 **CtlLayout**，因為 **Layout** 事件是在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 內定義的。  
  
## 請參閱  
 [如何：將 ActiveX 控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)   
 [Code Access Security](../../../../docs/framework/misc/code-access-security.md)   
 [Controls and Programmable Objects Compared in Various Languages and Libraries](http://msdn.microsoft.com/zh-tw/021f2a1b-8247-4348-a5ad-e1d9ab23004b)   
 [將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)   
 [Windows Form 控制項](../../../../docs/framework/winforms/controls/index.md)