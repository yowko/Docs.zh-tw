---
title: "x:Members Directive | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
caps.latest.revision: 5
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 5
---
# x:Members Directive
包含一組在標記中定義的成員，適用於父元素的 x:Class。  
  
## XAML Attribute Usage  
  
```  
  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`className`|XAML 生產支援類別或部分類別的名稱。  請參閱＜備註＞。|  
|`oneOrMoreMembers`|一個或多個代表成員定義的物件項目。  這些通常都是 `x:Property` 物件項目。  請參閱＜備註＞。|  
  
## 備註  
 在 .NET Framework XAML Services 服務實作中，沒有 `x:Members` 的支援類別或基本成員實作。  `x:Members` 是特殊的 XAML 成員，可以做為任何型別上的成員。  在 XAML 節點資料流中，`x:Members` 會在 XAML 語言 XAML 命名空間中表示成命名為 `Members` 的成員。  成員 `Members` 包含 `Member` 物件的唯讀泛型清單。  在典型的標記中, 個別成員指定為 `x:Property` 屬性項目。  `x:Property` 是特別用於型別屬性的更精確型別，可指派給 `x:Member`。  如需詳細資訊，請參閱 [x:Property Directive](../../../docs/framework/xaml-services/x-property-directive.md)。  
  
 若要支援實際使用 `x:Members` 做為在標記中指定成員定義的方法，這些成員必須與可修改的類別相關聯。  預期的模型是 `x:Members` 做為可指定 `x:Class` 之型別成員的形式存在。  但是，.NET Framework XAML Services 層級不支援關聯型別與成員或產生動態成員定義的機制。  這會保留給具有支援 XAML 成員定義之應用程式模型的個別架構。  通常需要 MSBUILD 建置動作以標記編譯 XAML，然後與程式碼後置整合，或是從 XAML 產生純組件，才能支援該功能。  
  
## Windows Workflow Foundation 的 x:Members  
 針對  Windows Workflow Foundation，`x:Members` 包含完全以 XAML 組成的自訂活動的成員，或者後置程式碼活動設計工具的 XAML 定義動態成員。  `x:Class` 也必須在 XAML 產物的根項目上指定。  這在 .NET Framework XAML 服務層級的需求，但是當 XAML 產物由支援自訂活動和 Windows Workflow Foundation XAML 的 MSBUILD 建置動作載入時，通常會變成需求。  `x:Members` 必須是宣告 `x:Class` 之物件項目標記中的第一個子項目。