---
title: "動態類型產生的可回收組件"
description: 
ms.date: 08/29/2017
ms.prod: .net
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0756fe317469898dd165e55be7125922f5b692f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>動態類型產生的可回收組件

「可回收組件」是動態組件，不需要卸載其建立所在的應用程式定義域即可予以卸載。 可以回收可回收組件所使用的所有受控和非受控記憶體與其包含的類型。 組件名稱這類資訊會從內部資料表中予以移除。

若要啟用卸載，請在建立動態組件時使用 <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> 旗標。 組件是暫時性 (也就是無法儲存它) 並受限於[可回收組件的限制](#restrictions-on-collectible-assemblies)一節中所述的限制。 通用語言執行平台 (CLR) 會在您發行所有與組件建立關聯的物件時自動卸載可回收組件。 在所有其他方面，可回收組件的建立和使用方式都會與其他動態組件相同。

## <a name="lifetime-of-collectible-assemblies"></a>可回收組件的存留期

可回收組件的存留期受控於是否有其所含類型以及從這些型別所建立之物件的參考。 只要有下列其中一或多個項目，通用語言執行平台就不會卸載組件 (`T` 是組件中定義的任何類型)： 

- `T` 的執行個體。

- `T` 陣列的執行個體。
 
- 將 `T` 作為它的其中一個型別引數的泛型型別執行個體。 這包含 `T` 的泛型集合，即使該集合是空的也是一樣。

- 表示 `T` 的 <xref:System.Type> 或 <xref:System.Reflection.Emit.TypeBuilder> 執行個體。 

   > [!IMPORTANT]
   > 您必須發行所有代表組件各部分的物件。 定義 `T` 的 <xref:System.Reflection.Emit.ModuleBuilder> 會保留 <xref:System.Reflection.Emit.TypeBuilder> 的參考，而 <xref:System.Reflection.Emit.AssemblyBuilder> 物件會保留 <xref:System.Reflection.Emit.ModuleBuilder> 的參考，因此必須發行這些物件的參考。 即使建構 `T` 時已使用 <xref:System.Reflection.Emit.LocalBuilder> 或 <xref:System.Reflection.Emit.ILGenerator> 還是會防止卸載。

- 依另一個動態定義型別 `T1` 之 `T` 的靜態參考，而此動態定義型別仍然可以透過執行程式碼來取得。 例如，`T1` 可能衍生自 `T`，或 `T` 可能是 `T1` 的方法中的參數類型。
 
- 屬於 `T` 之靜態欄位的 **ByRef**。

- <xref:System.RuntimeTypeHandle>、<xref:System.RuntimeFieldHandle> 或 <xref:System.RuntimeMethodHandle>，可以參考 `T` 或 `T` 的元件。

- 任何反映物件執行個體，可以間接或直接用來存取代表 `T` 的 <xref:System.Type> 物件。 例如，`T` 的 <xref:System.Type> 物件可以從其項目類型為 `T` 的陣列類型取得，或從具有 `T` 作為型別引數的泛型型別取得。 

- 任何執行緒呼叫堆疊上的方法 `M`，其中 `M` 是 `T` 的方法或是組件中所定義的模型層級方法。

- 定義於組件模組中之靜態方法的委派。

如果組件中的一個類型或一個方法在此清單中只有一個項目，則執行階段無法卸載組件。

> [!NOTE]
> 除非已針對清單中的所有項目執行完成項，否則執行階段不會實際卸載組件。

基於追蹤存留期的目的，會將產生可回收組件時所建立和使用的建構化泛型型別 (例如，C# 中的 `List<int>` 或 Visual Basic 中的 `List(Of Integer)`) 視為已定義在包含泛型型別定義的組件中，或包含它的其中一個型別引號定義的組件中。 使用的確切組件是實作詳細資料，而且可能會變更。
 
## <a name="restrictions-on-collectible-assemblies"></a>可回收組件的限制

下列限制適用於可回收組件： 

- **靜態參考**   
  一般動態組件中的類型不能有可回收組件中所定義型別的靜態參考。 例如，如果您定義繼承自可回收組件中類型的一般類型，則會擲回 <xref:System.NotSupportedException> 例外狀況。 可回收組件中的類型可以有另一個可回收組件中類型的靜態參考，但這會將已參考組件的存留期擴充為參考中組件的存留期。

- **COM Interop**   
   在可回收組件內無法定義 COM 介面，而且可回收組件內的型別執行個體無法轉換為 COM 物件。 可回收組件中的類型不能作為 COM 可呼叫包裝函式 (CCW) 或執行階段可呼叫包裝函式 (RCW)。 不過，可回收組件中的類型可以使用可實作 COM 介面的物件。

- **平台叫用**   
   具有 <xref:System.Runtime.InteropServices.DllImportAttribute> 屬性的方法在可回收組件中進行宣告時就不會進行編譯。 <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> 指令不能用於可回收組件中的類型實作，而且無法將此等類型封送處理至非受控碼。 不過，您可以使用非可回收組件中所宣告的進入點來呼叫原生程式碼。
 
- **封送處理**   
   無法封送處理可回收組件中所定義的物件 (特別是委派)。 這是所有暫時發出型別的限制。

- **組件載入**   
   反映發出是唯一支援載入可回收組件的機制。 無法卸載使用其他任何形式的組件載入所載入的組件。
 
- **內容繫結物件**    
   不支援內容靜態變數。 可回收組件中的類型無法擴充 <xref:System.ContextBoundObject>。 不過，可回收組件中的程式碼可以使用在其他位置定義的內容繫結物件。

- **執行緒靜態資料**       
   不支援執行緒靜態變數。

## <a name="see-also"></a>另請參閱

[發出動態方法和組件](emitting-dynamic-methods-and-assemblies.md)
