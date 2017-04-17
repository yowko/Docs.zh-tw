---
title: "x:Arguments Directive | Microsoft Docs"
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
  - "x:Arguments directive [XAML Services]"
  - "Arguments directive in XAML [XAML Services]"
  - "XAML [XAML Services], x:Arguments directive"
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
caps.latest.revision: 12
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 12
---
# x:Arguments Directive
在 XAML 中封裝非預設建構函式物件項目宣告的建構引數，或 Factory 方法物件宣告。  
  
## XAML 項目使用方式 \(非預設建構函式\)  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## XAML 項目使用方式 \(Factory 方法\)  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|一個或多個物件項目，這些項目會指定要傳遞給非預設支援建構函式或 Factory 方法的引數。<br /><br /> 一般的使用方式是使用物件項目中的初始化文字指定實際的引數值。  請參閱範例章節。<br /><br /> 項目的順序非常重要。  XAML 型別依序必須符合支援建構函式或 Factory 方法多載的型別及型別順序。|  
|`methodName`|應該會處理任何 `x:Arguments` 引數之 Factory 方法的名稱。|  
  
## 相依性  
 `x:FactoryMethod` 可以修改 `x:Arguments` 套用的範圍和行為。  
  
 如果未指定任何 `x:FactoryMethod`，`x:Arguments` 就會套用至支援建構函式的替代 \(非預設\) 簽章。  
  
 如果指定 `x:FactoryMethod`，`x:Arguments` 就會套用至具名方法的多載。  
  
## 備註  
 XAML 2006 可以透過初始化文字支援非預設初始化。  但是，初始化文字建構技術的實際應用是有限的。  初始化文字被視為單一文字字串；因此，只會增加單一參數初始化的功能，除非定義建構函式行為的型別轉換器，可以剖析字串的自訂資訊項目和自訂分隔符號。  而且，物件邏輯的文字字串可能是指定之 XAML 剖析器的處理基本型別的原生預設型別轉換子，而非真正的字串。  
  
 `x:Arguments` XAML 使用方式不是典型的屬性項目，因為指示詞標記不會參考包含物件項目的型別。  它近似於其他指示詞，例如 `x:Code`，其中項目會解除標記某個範圍，在此範圍中，應將標記解譯為預設子內容以外的內容。  在這種情況下，每個物件項目的 XAML 型別會傳達關於引數型別的資訊，由 XAML 剖析器用於判斷 `x:Arguments` 使用方法常是參考哪一個特定的建構函式原廠方法簽章。  
  
 建構中物件項的 `x:Arguments` 必須在物件項目的任何其他屬性項目、內容、內部文字或初始化字串之前。  `x:Arguments` 中的物件項目可以包含屬性和初始化字串，如該 XAML 型別及其支援建構函式或 Factory 方法所允許的。  對於物件或參數，您可以指定自訂 XAML 類型或 XAML 類型，這些類型可以透過參照建立的前置詞對應位於預設的 XAML 命名空間以外。  
  
 XAML 處理器使用下列方針，決定如何使用 `x:Arguments` 中指定的引數來建構物件。  如果指定 `x:FactoryMethod`，會比較資訊和指定的 `x:FactoryMethod`（請注意，`x:FactoryMethod` 的值是方法名稱，而且具名方法可以擁有多載。  如果未指定 `x:FactoryMethod`，會比較資訊與物件所有公開建構函式多載的集合。  然後 XAML 處理邏輯會比較參數的數目，並選取 Arity 相符 \(可接受同樣數目引數\) 的多載。  如果有多個相符項目，XAML 處理器應該根據所提供之物件項目的 XAML 型別比較參數的型別。  如果還有一個以上的相符項目，XAML 處理器行為就是未定義的。  如果指定`x:FactoryMethod`但無法解析該方法，XAML 處理器應擲回例外狀況。  
  
 XAML 屬性使用方式 `<x:Arguments>string</x:Arguments>` 在技術上是可行的。  不過，除了透過初始化文字和類型轉換器可執行的功能外，這不提供任何功能，而且，使用此語法不是 XAML 2009 原廠預設的方法功能。  
  
## 範例  
 下列範例顯示非預設建構函式簽章，然後說明存取該簽章之 `x:Arguments` 的 XAML 使用方式。  
  
```csharp  
public class Food {  
    private string _name;  
    private Int32 _calories;  
    public Food(string name, Int32 calories) {  
        _name=name;  
        _calories=calories;  
    }  
}  
```  
  
```  
<my:Food>  
    <x:Arguments>  
        <x:String>Apple</x:String>  
        <x:Int32>150</x:Int32>  
    </x:Arguments>  
</my:Food>  
```  
  
 下列範例顯示目標 Factory 方法簽章，然後說明存取該簽章之 `x:Arguments` 的 XAML 使用方式。  
  
```csharp  
public Food TryLookupFood(string name)  
{  
  switch (name) {  
    case "Apple": return new Food("Apple",150);  
    case "Chocolate": return new Food("Chocolate",200);  
    case "Cheese": return new Food("Cheese", 450);  
    default: {return new Food(name,0);  
  }  
}  
```  
  
```  
<my:Food x:FactoryMethod="TryLookupFood">  
    <x:Arguments>  
        <x:String>Apple</x:String>  
    </x:Arguments>  
</my:Food>  
```  
  
## 請參閱  
 [Defining Custom Types for Use with .NET Framework XAML Services](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)   
 [XAML 概觀 \(WPF\)](../../../ocs/framework/wpf/advanced/xaml-overview-wpf.md)