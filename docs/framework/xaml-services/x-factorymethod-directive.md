---
title: "x:FactoryMethod Directive | Microsoft Docs"
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
  - "XAML. x:FactoryMethod directive [XAML Services]"
  - "FactoryMethod directive in XAML [XAML Services]"
  - "x:FactoryMethod directive [XAML Services]"
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
caps.latest.revision: 8
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 8
---
# x:FactoryMethod Directive
指定方法，此方法不同於 XAML 處理器應在解析物件的支援型別之後用來初始化該物件的建構函式。  
  
## XAML 屬性使用方式，無 x:Arguments  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## XAML 屬性使用方式，x:引數為項目  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`methodname`|方法的字串方法名稱，XAML 處理器會呼叫此方法來初始化指定為 `object` 的執行個體。  請參閱＜備註＞。|  
|`oneOrMoreObjectElements`|指定 Factory 方法參數之物件的一或多個物件項目。  順序很重要，它表示將引數傳遞至 Factory 方法時應遵守的順序。|  
  
## 備註  
 如果 `methodname` 是執行個體方法，就會無法限定。  
  
 支援靜態方法做為 Factory 方法。  如果 `methodname` 是靜態方法，則會提供  `methodname` 做為 *typeName*.*methodName* 組合，其中 *typeName* 會為定義靜態 Factory 方法的類別命名。  如果參考對應 xmlns 中的型別，*typeName* 可以是前置詞限定。  *typeName* 可以是不同於 `typeof(``object``)` 的型別。  
  
 Factory 方法必須是支援相關物件項目之型別的已宣告公用方法。  
  
 Factory 方法必須傳回可指派至相關物件的執行個體。  Factory 方法不應傳回 null。  
  
 `x:Arguments` 會根據 Factory 方法簽章的最佳符合項目操作。  比對會先評估參數計數。  如果有一個以上可能的參數計數符合項目，會評估參數型別，然後決定最佳的符合項目。  如果在這個評估階段後仍模稜兩可，表示 XAML 處理器行為是未定義的。  
  
 `x:FactoryMethod` 項目使用方式不是典型的屬性項目，因為指示詞標記不會參考包含物件項目的型別。  項目使用方式應比屬性使用方式少見。  `x:Arguments` \(屬性或項目使用方式\) 可用於搭配 `x:FactoryMethod` 項目使用方式，但在使用方式章節中沒有明確顯示這點。  
  
 `x:FactoryMethod` 項目必須在任何其他屬性項目之前、必須在任何同樣為項目的 `x:Arguments` 之前，而且必須在任何內容\/內部文字\/初始化文字之前。  
  
## 請參閱  
 [x:Arguments Directive](../../../docs/framework/xaml-services/x-arguments-directive.md)