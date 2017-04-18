---
title: "複製和 Pin | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "複製, Interop 封送處理"
  - "Interop 封送處理, 複製"
  - "Interop 封送處理, Pin 動作"
  - "Pin 動作, Interop 封送處理"
ms.assetid: 0059f576-e460-4e70-b257-668870e420b8
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 複製和 Pin
封送處理資料時，Interop 封送處理器可以將要封送處理的資料複製或 Pin。  複製資料會將資料的複本從某一個記憶體位置放置到另一個記憶體位置。  下圖顯示複製實值型別與複製以傳址方式從 Managed 至 Unmanaged 記憶體傳遞的型別之間的差異。  
  
 ![以傳值和傳址方式傳遞的實值類型](../../../docs/framework/interop/media/interopmarshalcopy.gif "interopmarshalcopy")  
以傳值和傳址方式傳遞的實值型別  
  
 以傳值方式傳遞的方法引數是當成堆疊上的值封送處理至 Unmanaged 程式碼。  複製過程是直接的。  以傳址方式傳遞的引數是當成堆疊上的指標進行傳遞。  參考型別也是以傳值和傳址方式進行傳遞。  如下圖所示，會複製或 Pin 以傳值方式傳遞的參考型別。  
  
 ![COM Interop](../../../docs/framework/interop/media/interopmarshalpin.gif "interopmarshalpin")  
以傳值和傳址方式傳遞的參考型別  
  
 Pin 會暫時將資料鎖定在其目前的記憶體位置，因此可避免為 Common Language Runtime 的記憶體回收行程重新配置。  封送處理器會 Pin 資料來減少複製的固定成本並增強效能。  資料的型別會決定在封送處理時進行複製或 Pin。  在 <xref:System.String> 等這類物件的封送處理 \(Marshaling\) 期間會自動執行 Pin，但是您也可以使用 <xref:System.Runtime.InteropServices.GCHandle> 類別以手動方式 Pin 記憶體。  
  
## 格式化的 Blittable 類別  
 格式化的 [Blittable](../../../docs/framework/interop/blittable-and-non-blittable-types.md) 類別有固定的配置 \(已格式化\) 和 Managed 及 Unmanaged 記憶體中的一般資料表示。  當這些型別需要封送處理時，在堆積中的物件指標會直接傳遞到接收者。  接收者可以變更指標所參考的記憶體位置內容。  
  
> [!NOTE]
>  如果參數標示為 Out 或 In\/Out，被呼叫端便可以變更記憶體內容。  相較之下，當參數設為 In \(是格式化的 Blittable 型別之預設值\)，接收者應該避免變更內容。  當相同類別匯出至型別程式庫而且用來產生跨 Apartment 呼叫時，修改 In 物件會產生問題。  
  
## 格式化的非 Blittable 類別  
 格式化的[非 Blittable](../../../docs/framework/interop/blittable-and-non-blittable-types.md) 類別有固定的配置 \(已格式化\)，但在 Managed 及 Unmanaged 記憶體中資料表示是不同的。  在下列情況下資料可以要求轉換：  
  
-   如果非 Blittable 類別是以傳值方式封送處理，接收者會收到資料結構複本的指標。  
  
-   如果非 Blittable 類別是以傳址方式封送處理，接收者會收到資料結構複本指標的指標。  
  
-   如果設定 <xref:System.Runtime.InteropServices.InAttribute> 屬性，這個複本會永遠初始化為執行個體的狀態，並且在必要時進行封送處理。  
  
-   如果設定 <xref:System.Runtime.InteropServices.OutAttribute> 屬性，狀態會永遠在傳回時複製回執行個體，並且在必要時進行封送處理。  
  
-   如果設定 **InAttribute** 和 **OutAttribute**，則兩個複本都需要。  如果省略其中一個屬性，封送處理器便可以刪減任一複本來進行最佳化。  
  
## 參考型別  
 參考型別可以傳值和傳址方式進行傳遞。  當它們以傳值方式傳遞時，型別的指標會傳遞到堆疊上。  當以傳址方式傳遞時，型別指標的指標會傳遞到堆疊上。  
  
 參考型別具有以下條件式行為：  
  
-   如果參考型別是以傳值方式傳遞，而且有非 Blittable 型別的成員，則該型別會被轉換兩次：  
  
    -   在引數傳遞至 Unmanaged 端時。  
  
    -   在從呼叫返回時。  
  
     為了避免不必要的複製和轉換，這些型別會封送處理為 In 參數。  您必須明確地將 **InAttribute** 和 **OutAttribute** 屬性套用到呼叫端的引數中，以查看被呼叫端所做的變更。  
  
-   如果參考型別是以傳值方式傳遞，而且只有非 Blittable 型別的成員，則它在封送處理期間可以被 Pin，而且呼叫端可以看到接收者對型別的成員所做的任何變更。  如果您要這個行為，請明確套用 **InAttribute** 和 **OutAttribute**。  如果沒有這些方向屬性，Interop 封送處理器不會將方向性資訊匯出至型別程式庫 \(它會匯出成預設的 In\)，而且在 COM 跨 Apartment 封送處理中會發生問題。  
  
-   如果參考型別是以傳址方式傳遞，則預設會封送處理為 In\/Out。  
  
## System.String 和 System.Text.StringBuilder  
 當資料是以傳值或傳址方式封送處理至 Unmanaged 程式碼時，封送處理器一般會將資料複製至次要緩衝區 \(也許會在複製期間轉換字元集\)，並將緩衝區的參考傳遞到接收者。  除非參考是以 **SysAllocString** 配置的 **BSTR**，否則參考會固定以 **CoTaskMemAlloc** 配置。  
  
 因為最佳化因素，當任一字串型別 \(如 Unicode 字元字串\) 是以傳值方式封送處理時，封送處理器會在內部 Unicode 緩衝區中將 Managed 字串的直接指標傳遞給接收者，而不是將其複製到新的緩衝區。  
  
> [!CAUTION]
>  當字串是以傳值方式傳遞時，被呼叫端不可以更改封送處理器傳遞的參考。  這麼做的話可能會破壞 Managed 堆積。  
  
 當 <xref:System.String?displayProperty=fullName> 是以傳址方式傳遞時，封送處理器會在產生呼叫之前將字串內容複製到次要緩衝區。  然後它會在從呼叫返回時將緩衝區的內容複製到新的字串中。  這個方法可確保不變的 Managed 字串保持不變。  
  
 當 <xref:System.Text.StringBuilder?displayProperty=fullName> 是以傳值方式傳遞時，封送處理器會直接將 **StringBuilder** 的內部緩衝區參考傳遞到呼叫端。  呼叫端和接收者的緩衝區的大小必須一致。  呼叫端負責建立足夠長度的 **StringBuilder**。  而接收者必須採取必要的預防措施來確保緩衝區超越限度。  **StringBuilder** 是以傳值方式傳遞的參考型別之規則的例外，參考型別預設會傳遞為 In 參數。  而它永遠傳遞為 In\/Out。  
  
## 請參閱  
 [預設的封送處理行為](../../../docs/framework/interop/default-marshaling-behavior.md)   
 [Memory Management with the Interop Marshaler](http://msdn.microsoft.com/zh-tw/417206ce-ee3e-4619-9529-0c0b686c7bee)   
 [Directional Attributes](http://msdn.microsoft.com/zh-tw/241ac5b5-928e-4969-8f58-1dbc048f9ea2)   
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)