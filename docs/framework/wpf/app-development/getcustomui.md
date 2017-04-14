---
title: "GetCustomUI | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自訂的錯誤訊息 [WPF]"
  - "GetCustomUI 方法"
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# GetCustomUI
透過 PresentationHost.exe 呼叫，用以取得來自主應用程式 \(Host\) 的自訂進度和錯誤訊息 \(如果已實作\)。  
  
## 語法  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
#### 參數  
 `pwzProgressAssemblyName`  
  
 \[out\] 包含主應用程式提供之進度使用者介面的組件 \(Assembly\) 指標。  
  
 `pwzProgressClassName`  
  
 \[out\] 為主應用程式提供之進度使用者介面的類別名稱，而它的最上層項目最好是具有 <xref:System.Windows.Controls.Page> 的 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 檔案。  這個類別是位在 `pwzProgressAssemblyName` 指定的組件中。  
  
 `pwzErrorAssemblyName`  
  
 \[out\] 包含主應用程式提供之錯誤使用者介面的組件指標。  
  
 `pwzErrorClassName`  
  
 \[out\] 主應用程式提供之錯誤使用者介面的類別名稱，而它的最上層項目最好是具有 <xref:System.Windows.Controls.Page> 的 XAML 檔案。  這個類別是位在 `pwzErrorAssemblyName` 指定的組件中。  
  
## 屬性值\/傳回值  
 HRESULT：忽略。  
  
## 備註  
 主應用程式 \(Host Application\) 可能會有 PresentationHost.exe 預設使用者介面未遵循的特定佈景主題。  如果是這種情況，則主應用程式可以實作 [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md)，以將進度和錯誤使用者介面傳回給 PresentationHost.exe。  PresentationHost.exe 一律會先呼叫 [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md)，再使用它的預設使用者介面。  
  
 這個函式會在 PresentationHost 初始設定期間呼叫一次  
  
## 請參閱  
 [IWpfHostSupport](../../../../docs/framework/wpf/app-development/iwpfhostsupport.md)