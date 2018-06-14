---
title: 以程式設計方式使用 .resx 檔案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resource files, .resx files
- .resx files
ms.assetid: 168f941a-2b84-43f8-933f-cf4a8548d824
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 569f2d59bb2abf013a87bdaa694a7fcf36c70042
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398829"
---
# <a name="working-with-resx-files-programmatically"></a>以程式設計方式使用 .resx 檔案
因為 XML 資源 (.resx) 檔必須由妥善定義的 XML 組成，而其中所包含的標頭，需遵循特定結構描述且後面接著名稱/值組的資料，可能您會認為以手動方式建立這些檔案容易出錯。 另一種方法是，您可以使用 .NET Framework Class Library 中的型別和成員，透過程式設計的方式建立 .resx 檔。 您也可以使用 .NET Framework Class Library 擷取儲存在 .resx 檔中的資源。 本主題說明如何使用 <xref:System.Resources> 命名空間中的型別和成員，來處理 .resx 檔。  
  
 請注意，本文探討的是含有資源之 XML (.resx) 檔的運用。 如需使用已內嵌於組件的二進位資源檔相關資訊，請參閱 <xref:System.Resources.ResourceManager> 主題。  
  
> [!WARNING]
>  除了透過程式設計之外，還有其他運用 .resx 檔的方法。 當您將資源檔加入至 Visual Studio 專案時，Visual Studio 會提供介面讓您建立和維護 .resx 檔，並於編譯時間自動將 .resx 檔轉換成 .resources 檔。 您也可以使用文字編輯器直接操作 .resx 檔。 不過，為避免損毀檔案，請小心別更動任何儲存在檔案中的二進位資訊。  
  
## <a name="creating-a-resx-file"></a>建立 .resx 檔  
 您可以使用 <xref:System.Resources.ResXResourceWriter?displayProperty=nameWithType> 類別執行下列步驟，以程式設計方式建立 .resx 檔：  
  
1.  呼叫 <xref:System.Resources.ResXResourceWriter> 方法並提供 .resx 檔的名稱，具現化 <xref:System.Resources.ResXResourceWriter.%23ctor%28System.String%29?displayProperty=nameWithType> 物件。 檔案名稱必須包含 .resx 這個副檔名。 如果您是在 <xref:System.Resources.ResXResourceWriter> 區塊中具現化 `using` 物件，則您不必非得呼叫步驟 3 的 <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> 方法。  
  
2.  針對您要加入檔案的每個資源呼叫 <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> 方法。 使用此方法的多載功能加入字串、物件和二進位檔 (位元組陣列) 資料。 如果資源是物件，它必須可以序列化。  
  
3.  呼叫 <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> 方法以產生資源檔並釋放所有資源。 如果 <xref:System.Resources.ResXResourceWriter> 物件是在 `using` 區塊中建立，則資源會寫入 .resx 檔，且 <xref:System.Resources.ResXResourceWriter> 物件所使用的資源會在 `using` 區塊的結尾釋放。  
  
 產生的 .resx 檔具有適當的標頭以及 `data` 方法所加入之每個資源的 <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> 標記。  
  
> [!WARNING]
>  請勿使用資源檔儲存密碼、安全機密資訊或私用資料。  
  
 下列範例會建立名為 CarResources.resx 的.resx 檔，其中儲存六個字串、一個圖示和兩個應用程式定義的物件 (兩個 `Automobile` 物件)。 請注意，範例中所定義和具現化的 `Automobile` 類別，會標記為 <xref:System.SerializableAttribute> 屬性。  
  
 [!code-csharp[Conceptual.Resources.ResX#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/create1.cs#1)]
 [!code-vb[Conceptual.Resources.ResX#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/create1.vb#1)]  
  
> [!IMPORTANT]
>  您也可以使用 Visual Studio 建立 .resx 檔。 Visual Studio 會在編譯時期使用 [資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 將 .resx 檔轉換成二進位資源 (.resources) 檔，並將其內嵌在應用程式組件或附屬組件中。  
  
 您無法將 .resx 檔內嵌於執行階段可執行檔，或將其編譯至附屬組件中。 您必須使用 [資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)將 .resx 檔轉換成二進位資源 (.resources) 檔。 產生的 .resources 檔接著可內嵌於應用程式組件或附屬組件中。 如需詳細資訊，請參閱 [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)。  
  
## <a name="enumerating-resources"></a>列舉資源  
 在某些情況下，您可能會想從 .resx 檔擷取所有資源，而非特定資源。 若要這樣做，您可以使用 <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> 類別，此類別會在 .resx 檔中提供所有資源的列舉值。 <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> 類別會實作 <xref:System.Collections.IDictionaryEnumerator>，並傳回 <xref:System.Collections.DictionaryEntry> 物件，表示每個在迴圈中反覆運算的特定資源。 其 <xref:System.Collections.DictionaryEntry.Key%2A?displayProperty=nameWithType> 屬性會傳回資源的索引鍵，且其 <xref:System.Collections.DictionaryEntry.Value%2A?displayProperty=nameWithType> 屬性會傳回資源的值。  
  
 下列範例會針對上一個範例中所建立的 CarResources.resx 檔建立 <xref:System.Resources.ResXResourceReader> 物件，並透過資源檔逐一查看。 它會將資源檔中所定義的兩個 `Automobile` 物件加入 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 物件中，並將六個字串的其中五個加入 <xref:System.Collections.SortedList> 物件。 <xref:System.Collections.SortedList> 物件中的值會轉換到用來對主控台顯示欄位標題的參數陣列。 `Automobile` 屬性值也會顯示到主控台。  
  
 [!code-csharp[Conceptual.Resources.ResX#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/enumerate1.cs#2)]
 [!code-vb[Conceptual.Resources.ResX#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/enumerate1.vb#2)]  
  
## <a name="retrieving-a-specific-resource"></a>擷取特定的資源  
 除了列舉 .resx 檔中的項目之外，您也可以使用 <xref:System.Resources.ResXResourceSet?displayProperty=nameWithType> 類別依名稱擷取特定的資源。 <xref:System.Resources.ResourceSet.GetString%28System.String%29?displayProperty=nameWithType> 方法會擷取具名字串資源的值。 <xref:System.Resources.ResourceSet.GetObject%28System.String%29?displayProperty=nameWithType> 方法會擷取具名物件或二進位資料的值。 方法會傳回物件，接著該物件必須 (在 C# 中) 進行轉換或 (在 Visual Basic 中) 轉換成適當型別的物件。  
  
 下列範例會依其資源名稱擷取某個表單的標題字串和圖示。 它也會擷取前一個範例中所使用之應用程式定義的 `Automobile` 物件，並在 <xref:System.Windows.Forms.DataGridView> 控制項顯示這些物件。  
  
 [!code-csharp[Conceptual.Resources.ResX#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/retrieve1.cs#3)]
 [!code-vb[Conceptual.Resources.ResX#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/retrieve1.vb#3)]  
  
## <a name="converting-resx-files-to-binary-resources-files"></a>將 .resx 檔轉換成二進位 .resources 檔  
 將 .resx 檔轉換成內嵌二進位資源 (.resources) 檔案有很大的好處。 雖然 .resx 檔在應用程式開發過程易於閱讀及維護，但是這種檔案很少會包含在已完成的應用程式中。 如果它們經由應用程式散發，就會從應用程式執行檔及其隨附的程式庫中分離出來，成為單獨的檔案。 相較之下，.resources 檔則會內嵌在應用程式執行檔或其隨附的組件中。 此外，以當地語系化的應用程式而言，若要在執行階段仰賴 .resx 檔，就得靠開發人員負責處理資源後援。 與之相反的是，假如已經建立一組含有內嵌 .resources 檔的附屬組件，Common Language Runtime 就會負責處理資源後援程序。  
  
 若要將 .resx 檔轉換成 .resources 檔，您可以使用 [資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)，它基本語法如下：  
  
 **Resgen.exe** *.resxFilename*  
  
 結果是一個二進位資源檔，具有與 .resx 檔相同的根檔名和 .resources 檔的副檔名。 這個檔案可以在編譯時間編譯到執行檔或程式庫中。 如果您使用的是 Visual Basic 編譯器，請使用下列語法在應用程式的執行檔中內嵌 .resources 檔：  
  
 **vbc** *filename* **.vb -resource:** *.resourcesFilename*  
  
 如果您使用的是 C#，其語法如下：  
  
 **csc** *filename* **.cs -resource:** *.resourcesFilename*  
  
 您也可以利用 [組件連結器 (AL.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md)將 .resources 檔內嵌於附屬組件中，其基本語法如下：  
  
 **al** *resourcesFilename* **-out:** *assemblyFilename*  
  
## <a name="see-also"></a>請參閱  
 [建立資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Resgen.exe (資源檔產生器)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 [Al.exe (組件連結器)](../../../docs/framework/tools/al-exe-assembly-linker.md)
