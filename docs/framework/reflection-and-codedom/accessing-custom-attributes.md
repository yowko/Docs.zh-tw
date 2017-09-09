---
title: "存取自訂屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "屬性 [.NET Framework], 存取"
  - "自訂屬性, 網頁可及性"
  - "反映, 自訂屬性"
ms.assetid: 1d8e3398-00d8-47d5-a084-214f9859d3d7
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# 存取自訂屬性
在屬性已經與程式項目關聯之後，反映可以用來查詢它們的存在和值。  在 .NET Framework 1.0 和 1.1 版中，會在執行內容中檢查自訂屬性。  .NET Framework 2.0 版提供了新的載入內容，這是僅限反映的內容，可用來檢查無法載入來執行的程式碼。  
  
## 僅限反映的內容  
 載入到僅限反映的內容中之程式碼無法加以執行；  這表示無法建立自訂屬性的執行個體，因為這將需要執行其建構函式。  若要載入及檢查僅限反映的內容中的自訂屬性，請使用 <xref:System.Reflection.CustomAttributeData> 類別。  您可以使用靜態 <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=fullName> 方法的適當多載，藉以取得這個類別的執行個體。  請參閱 [如何：將組件載入僅限反映的內容](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)。  
  
## 執行內容  
 執行內容中查詢屬性的主要反映方法為 <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=fullName> 與 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=fullName>。  
  
 自訂屬性的存取範圍針對它所附加的組件來檢查。  這等於檢查自訂屬性所附加的組件型別中之方法，是否可以呼叫自訂屬性 \(Attribute\) 的建構函式。  
  
 類似 <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=fullName> 的方法會檢查型別引數的可視性和存取範圍。  只有包含使用者定義型別的組件中的程式碼可以使用 **GetCustomAttributes** 擷取該型別的自訂屬性。  
  
 下列 C\# 範例是典型的自訂屬性設計模式。  它說明 Runtime 自訂屬性反映模型。  
  
```  
System.DLL  
public class DescriptionAttribute : Attribute  
{  
}  
  
System.Web.DLL  
internal class MyDescriptionAttribute : DescriptionAttribute  
{  
}  
  
public class LocalizationExtenderProvider  
{  
    [MyDescriptionAttribute(...)]  
    public CultureInfo GetLanguage(...)  
    {  
    }  
}  
```  
  
 如果 Runtime 嘗試擷取附加至 **GetLanguage** 方法之公用自訂屬性型別 <xref:System.ComponentModel.DescriptionAttribute> 的自訂屬性，它便會執行下列動作：  
  
1.  執行階段會檢查 **Type.GetCustomAttributes** \(型別 *type*\) 的型別引數 **DescriptionAttribute** 是否為公用；如果是公用，則為可見及可存取。  
  
2.  Runtime 會檢查從 **DescriptionAttribute** 衍生的使用者定義型別 **MyDescriptionAttribute** 在 **System.Web.DLL** 組件 \(它是在這個組件中附加至 **GetLanguage**\(\) 方法\) 內是否為可見和可存取。  
  
3.  Runtime 會檢查 **MyDescriptionAttribute** 的建構函式在 **System.Web.DLL** 組件內是否為可見和可存取。  
  
4.  Runtime 會以自訂屬性參數呼叫 **MyDescriptionAttribute** 的建構函式，並將新物件傳回呼叫端。  
  
 自訂屬性反映模型可能會將使用者定義型別的執行個體遺漏在定義型別所在的組件之外。  這無異於執行階段系統程式庫中會傳回使用者定義型別執行個體的成員，例如，傳回 **RuntimeMethodInfo** 物件陣列的 [Type.GetMethods\(\)](frlrfSystemTypeClassGetMethodsTopic)。  若要防止用戶端探索關於使用者定義自訂屬性型別的資訊，請將型別的成員定義為非公用。  
  
 下列範例示範使用反映存取自訂屬性的基本方式。  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## 請參閱  
 <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=fullName>   
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=fullName>   
 [檢視類型資訊](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)   
 [反映的安全性考量](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)