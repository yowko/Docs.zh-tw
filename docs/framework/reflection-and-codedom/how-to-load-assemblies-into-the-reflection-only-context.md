---
title: "如何：將組件載入僅限反映的內容 | Microsoft Docs"
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
  - "組件 [.NET Framework], 載入以反映"
  - "組件 [.NET Framework], 僅限反映的載入器內容"
  - "屬性 [.NET Framework], 擷取"
  - "反映, 僅限反映的載入器內容"
  - "僅限反映的載入器內容"
ms.assetid: 9818b660-52f5-423d-a9af-e75163aa7068
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：將組件載入僅限反映的內容
僅限反映的載入內容可讓您檢查針對其他平台或其他版本的 .NET Framework 所編譯的組件。  載入此內容中的程式碼只能夠被檢查，而無法被執行；  這表示無法建立物件，因為無法執行建構函式。  由於此程式碼無法被執行，所以不會自動載入相依性。  如果您需要檢查這些相依性，則必須自行載入。  
  
### 若要將組件載入到僅限反映的載入內容中  
  
1.  使用 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> 方法多載來載入組件 \(在有提供它的顯示名稱時\)，或是使用 <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> 方法來載入組件 \(在有提供它的路徑時\)。  如果這個組件是二進位檔映像，請使用 [ReflectionOnlyLoad\(Byte\<xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> 方法多載。  
  
    > [!NOTE]
    >  您無法使用僅限反映的內容從執行內容中的版本以外的 .NET Framework 版本載入一個 mscorlib.dll 版本。  
  
2.  如果組件有相依性，則 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> 方法不會載入這些相依性。  如果您需要檢查這些相依性，則必須自行載入。  
  
3.  判斷是否利用某個組件的 <xref:System.Reflection.Assembly.ReflectionOnly%2A> 屬性，而將這個組件載入到僅限反映的內容中。  
  
4.  如果屬性已經套用到這個組件或組件中的型別，請使用 <xref:System.Reflection.CustomAttributeData> 類別來檢查這些屬性，以確定沒有人嘗試要執行僅限反映的內容中的程式碼。  請使用 <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=fullName> 方法的適當多載來取得 <xref:System.Reflection.CustomAttributeData> 物件，此物件表示套用到組件、成員、模組或參數的屬性。  
  
    > [!NOTE]
    >  套用到這個組件或其內容的屬性可以定義在這個組件中，也可以定義在另一個載入到僅限反映的內容中的組件內。  但是，無法事先知道這些屬性要定義於何處。  
  
## 範例  
 下列程式碼範例將示範如何檢查已套用到組件中的屬性 \(這個組件已載入到僅限反映的內容中\)。  
  
 此程式碼範例將定義具有兩個建構函式和一個屬性 \(Property\) 的自訂屬性 \(Attribute\)，  這個屬性 \(Attribute\) 會套用到此組件、此組件中宣告的型別、此型別的方法，以及此方法的參數。  當這個組件執行時，會將它本身載入到僅限反映的內容中，並顯示與自訂屬性有關的資訊 \(是指套用到這個組件以及它所包含的型別和成員的屬性\)。  
  
> [!NOTE]
>  為了簡化此程式碼範例，這個組件會自行載入及檢查。  一般來說，您應該不會找到可以同時載入到執行內容和僅限反映的內容中的相同組件。  
  
 [!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
 [!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
 [!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]  
  
## 請參閱  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>   
 <xref:System.Reflection.Assembly.ReflectionOnly%2A>   
 <xref:System.Reflection.CustomAttributeData>