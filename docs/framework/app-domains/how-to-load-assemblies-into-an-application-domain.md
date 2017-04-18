---
title: "如何：將組件載入應用程式定義域 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "應用程式定義域, 載入組件"
  - "載入組件"
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：將組件載入應用程式定義域
將組件載入應用程式定義域的方式有好幾種，  建議的方式是使用 [System.Reflection.Assembly](https://msdn.microsoft.com/en-us/library/system.reflection.aspx) 類別的 `static` \(在 Visual Basic 中為 `Shared`\) <xref:System.Reflection.Assembly.Load%2A> 方法。  載入組件的其他方式包括：  
  
-   [Assembly](https://msdn.microsoft.com/en-us/library/system.reflection.aspx) 類別的 <xref:System.Reflection.Assembly.LoadFrom%2A> 方法會載入提供檔案位置的組件。  以此方法載入組件時，會使用不同的載入內容。  
  
-   <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> 和 <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> 方法可將組件載入僅限反映的內容中。  載入此內容中的組件可以進行檢查但不能加以執行，以允許檢查以其他平台為目標的組件。  請參閱 [如何：將組件載入僅限反映的內容](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)。  
  
> [!NOTE]
>  僅限反映的內容是 .NET Framework 2.0 版中所新增。  
  
-   類似 <xref:System.AppDomain> 類別的 <xref:System.AppDomain.CreateInstance%2A> 和 <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> 方法，可以將組件載入應用程式定義域中。  
  
-   <xref:System.Type> 類別的 <xref:System.Type.GetType%2A> 方法可載入組件。  
  
-   <xref:System.AppDomain?displayProperty=fullName> 類別的 <xref:System.AppDomain.Load%2A> 方法可以載入組件，但主要用於 COM 互通性 \(Interoperability\)。  您不應該使用這個方法將組件載入呼叫此方法之應用程式定義域以外的應用程式定義域中。  
  
> [!NOTE]
>  從 .NET Framework 2.0 版開始，如果使用比目前載入之執行階段版本還要高的 .NET Framework 版本來編譯組件，則執行階段將不會載入這個組件。  這種情形適用於版本號碼的主要和次要元件組合。  
  
 您可以指定 Just\-in\-Time \(JIT\) 從載入的組件編譯程式碼的方式就是在應用程式定義域之間共用。  如需詳細資訊，請參閱[Application Domains and Assemblies](http://msdn.microsoft.com/zh-tw/433b04ae-4ba8-4849-9dbd-79194f240346)。  
  
## 範例  
 下列程式碼會將名為 "example.exe" 或 "example.dll" 的組件載入目前的應用程式定義域中、從該組件取得名為 `Example` 的型別、為該型別取得名為 `MethodA` 的無參數方法，並執行該方法。  如需取得載入組件資訊的完整討論，請參閱[動態載入和使用型別](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md)。  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## 請參閱  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>   
 [Hosting Overview](http://msdn.microsoft.com/zh-tw/ea527626-99e3-4995-81c4-c8f3e60eb6d5)   
 [Programming with Application Domains](http://msdn.microsoft.com/zh-tw/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [反映](../../../docs/framework/reflection-and-codedom/reflection.md)   
 [使用應用程式定義域](../../../docs/framework/app-domains/use.md)   
 [如何：將組件載入僅限反映的內容](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)   
 [Application Domains and Assemblies](http://msdn.microsoft.com/zh-tw/433b04ae-4ba8-4849-9dbd-79194f240346)