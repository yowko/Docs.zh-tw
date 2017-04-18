---
title: "Visual Studio 2012 的識別和存取工具 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 87b8f8f2-4074-44fd-9fd6-08278e877390
caps.latest.revision: 3
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 3
---
# Visual Studio 2012 的識別和存取工具
本主題說明適用於 Visual Studio 11 的新識別和存取工具。  您可以從下列 URL 下載此工具：[http:\/\/go.microsoft.com\/fwlink\/?LinkID\=245849](http://go.microsoft.com/fwlink/?LinkID=245849)。或者，您也可以直接在 Visual Studio 11 的擴充管理員中搜尋「識別」以取得此工具。  
  
 適用於 Visual Studio 11 的新識別和存取工具具有下列優點，可大幅簡化開發時間：  
  
-   使用這項新工具，您可以使用 Web 應用程式專案類型並以 IIS Express 為目標進行開發。  
  
-   這項新工具與僅具有保護功能的驗證方式不同，您可以指定本機主領域探索頁面\/控制站 \(或是在應用程式中處理驗證經驗的其他端點\)，而 WIF 會將所有未驗證的要求都設定為移至該頁面\/控制站，而不是將這些頁面重新導向至 STS。  
  
-   此工具包含測試 Security Token Service \(STS\)，當您啟動偵錯工作階段時，STS 隨即在您的本機電腦上執行。  因此，您不必再建立自訂和調整 STS 專案，就可以取得測試應用程式所需的宣告。  宣告類型和值都開放完全自訂。  
  
-   您可以直接透過工具的 UI 修改一般設定，而不必編輯 web.config。  
  
-   您可以在單一螢幕中，利用 Active Directory Federation Services \(AD FS\) 2.0 \(或其他 WS\-Federation 提供者\) 建立同盟。  
  
-   此工具會利用 Microsoft Azure Access Control Service \(ACS\) 功能並提供簡易核取方塊清單，其中列出您要使用的所有識別提供者：Facebook、Google、Live ID、Yahoo\!、所有 OpenID 提供者以及所有 WS\-Federation 提供者。  只要選取識別提供者、按一下 \[確定\]，然後按 F5，您的應用程式和 ACS 即可自動設定完成，成為 ACS 感知測試應用程式。  
  
## 請參閱  
 [WIF 功能](../../../docs/framework/security/wif-features.md)