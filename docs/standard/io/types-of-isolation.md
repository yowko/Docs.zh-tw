---
title: "隔離的類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- storing data using isolated storage, accessing isolated storage
- storing data using isolated storage, isolation types
- authentication [.NET Framework], isolated storage
- assemblies [.NET Framework], identity
- isolated storage, accessing
- data storage using isolated storage, isolation types
- data storage using isolated storage, accessing isolated storage
- domain identity
- isolated storage, types
- user authentication, isolated storage
ms.assetid: 14812988-473f-44ae-b75f-fd5c2f21fb7b
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6b07c090a381925f5330a820214126a121d3790b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="types-of-isolation"></a>隔離的類型
存取隔離儲存區永遠僅限於建立它之使用者的。 若要實作這種類型的隔離，通用語言執行平台使用相同作業系統辨識出的使用者身分識別的概念與開啟存放區時，程式碼執行所在的處理序相關聯的識別。 這個身分識別是一個已驗證的使用者的身分識別，但是模擬可能會以動態方式變更目前使用者的身分識別。  
  
 存取隔離儲存區也是根據與應用程式定義域和組件，或單獨的組件相關聯的身分識別來限制。 執行階段會以下列方式取得這些身分識別：  
  
-   定義域識別代表應用程式，這在 web 應用程式的情況下可能會是完整的 URL 辨識的項。 殼層裝載程式碼的定義域識別可能會根據應用程式的目錄路徑。 例如，如果可執行檔將會從路徑 C:\Office\MyApp.exe 網域身分識別將 C:\Office\MyApp.exe。  
  
-   組件的辨識項組件識別。 這可能來自於密碼編譯數位簽章，它可以是組件的[強式名稱](../../../docs/framework/app-domains/strong-named-assemblies.md)，組件或它的 URL 識別的軟體發行者。 如果組件具有強式名稱和軟體發行者身分識別，則會使用軟體發行者身分識別。 如果組件來自網際網路，且不帶正負號，將使用的 URL 識別。 如需組件和強式名稱的詳細資訊，請參閱[使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)。  
  
-   漫遊存放區移動與使用者具有漫遊使用者設定檔。 檔案會寫入至網路目錄，並會下載到任何電腦在使用者登入。 如需漫遊使用者設定檔的詳細資訊，請參閱<xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>。  
  
 藉由結合使用者、 定義域和組件識別的概念，隔離儲存區可以隔離資料，在下列方面，每一個都有它自己的使用案例：  
  
-   [依據使用者和組件的隔離。](#UserAssembly)  
  
-   [依據使用者、 定義域和組件的隔離。](#UserDomainAssembly)  
  
 其中一個這些任一個都可以結合漫遊使用者設定檔。 如需詳細資訊，請參閱下節[隔離儲存區並漫遊](#Roaming)。  
  
 下圖示範如何將存放區隔離在不同範圍中。  
  
 ![依據使用者和組件的隔離](../../../docs/standard/io/media/typesofisolation.gif "typesofisolation")  
隔離儲存區的類型  
  
 請注意，除了漫遊存放區，隔離儲存區一律以隱含方式隔離的電腦因為它會使用指定的電腦本機的儲存體功能。  
  
> [!IMPORTANT]
>  [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式無法使用隔離儲存區。 請改用 `Windows.Storage` 應用程式開發介面內含的 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 命名空間中的應用程式資料類別來儲存本機資料和檔案。 如需詳細資訊，請參閱 Windows 開發人員中心的 [應用程式資料](http://go.microsoft.com/fwlink/?LinkId=229175) 。  
  
<a name="UserAssembly"></a>   
## <a name="isolation-by-user-and-assembly"></a>依據使用者和組件的隔離。  
 當使用資料的組件儲存為可從任何應用程式定義域，依據使用者和組件的隔離是適當的需求。 通常，在此情況下，隔離儲存區用來儲存適用於多個應用程式，以及未繫結至任何特定的應用程式，例如使用者名稱或授權資訊的資料。 若要存取使用者和組件所隔離儲存區，程式碼必須是受信任的應用程式之間傳輸資訊。 一般而言，使用者和組件所隔離允許內部網路，但不是在網際網路上。 呼叫靜態<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType>方法，並將使用者和組件<xref:System.IO.IsolatedStorage.IsolatedStorageScope>傳回與這種隔離的存放裝置。  
  
 下列程式碼範例會擷取使用者和組件所隔離的存放區。 在存放區可以透過存取`isoFile`物件。  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 如需使用辨識項參數的範例，請參閱<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>方法可做為快顯，如下列程式碼範例所示。 這個捷徑不能用來開啟能夠漫遊; 的存放區使用<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>在此情況下。  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## <a name="isolation-by-user-domain-and-assembly"></a>依據使用者、 定義域和組件的隔離。  
 如果您的應用程式使用協力廠商組件需要私用資料存放區，您可以使用隔離儲存區來儲存的私用資料。 依據使用者、 定義域和組件的隔離，可確保只有指定的組件中的程式碼可以存取資料，和只有在組件由應用程式執行時建立的組件存放區，且只在的使用者存放區已建立其執行時，才 應用程式。 依據使用者、 定義域和組件的隔離會保留不外洩資料給其他應用程式的協力廠商組件。 這個隔離類型應該是預設選擇，如果您知道您想要使用隔離儲存區，但不確定哪一種隔離使用。 呼叫靜態<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>方法<xref:System.IO.IsolatedStorage.IsolatedStorageFile>並傳入使用者、 定義域和組件<xref:System.IO.IsolatedStorage.IsolatedStorageScope>傳回與這種隔離的存放裝置。  
  
 下列程式碼範例會擷取使用者、 定義域和組件所隔離的存放區。 在存放區可以透過存取`isoFile`物件。  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 下列程式碼範例所示，請使用另一種方法。 這個捷徑不能用來開啟能夠漫遊; 的存放區使用<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>在此情況下。  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## <a name="isolated-storage-and-roaming"></a>隔離儲存區並漫遊  
 漫遊使用者設定檔是 Windows 功能，可讓使用者設定網路上的身分識別，並使用該識別來登入的任何網路電腦，執行於所有的個人化設定。 使用隔離儲存區的組件可以指定使用者的隔離儲存區應該與漫遊使用者設定檔。 漫遊可以連同依據使用者和組件的隔離或隔離使用由使用者、 定義域和組件。 如果未使用漫遊的範圍，將不會漫遊存放區，即使使用漫遊使用者設定檔。  
  
 下列程式碼範例會擷取使用者和組件所隔離的漫遊存放區。 在存放區可以透過存取`isoFile`物件。  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 若要建立依據使用者、 定義域和應用程式隔離的漫遊存放區，可以加入網域範圍。 下列程式碼範例為其示範。  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [隔離儲存區](../../../docs/standard/io/isolated-storage.md)
