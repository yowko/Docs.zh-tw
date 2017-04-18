---
title: "隔離的類型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "使用隔離儲存區儲存資料，存取隔離儲存區"
  - "使用隔離儲存區儲存資料，隔離類型"
  - "驗證 [.NET Framework]，隔離儲存區"
  - "組件 [.NET Framework]，身分識別"
  - "隔離儲存區，存取"
  - "使用隔離儲存區的資料儲存區，隔離類型"
  - "使用隔離儲存區的資料儲存區，存取隔離儲存區"
  - "定義域識別"
  - "隔離儲存區，類型"
  - "使用者驗證，隔離儲存區"
ms.assetid: 14812988-473f-44ae-b75f-fd5c2f21fb7b
caps.latest.revision: 16
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 16
---
# 隔離的類型
隔離儲存區永遠只限建立它的使用者來存取。  為了要實作這個隔離類型，Common Language Runtime 使用作業系統能辨識的使用者識別 \(存放區開啟時，與執行程式碼的處理序相關聯的識別\) 的相同概念。  這個識別為已驗證的使用者識別，但模擬可能導致目前使用者的識別動態地變更。  
  
 除了被使用者隔離外，隔離儲存區 \(Isolated Storage\) 的存取也會根據與應用程式定義域和組件 \(或僅組件\) 關聯的識別 \(Identity\) 而有所限制。  執行階段會以下列方式取得這些識別：  
  
-   定義域識別代表應用程式的辨識項，在 Web 應用程式的案例中可能是完整的 URL。  對於 shell 裝載的程式碼，定義域識別可能是根據應用程式目錄路徑。  例如，如果可執行檔從路徑 C:\\Office\\MyApp.exe 執行，定義域識別將是 C:\\Office\\MyApp.exe。  
  
-   組件識別為組件的辨識項。  這個可能來自密碼編譯數位簽章，可能是組件的[強式名稱](../../../docs/framework/app-domains/strong-named-assemblies.md)、組件的軟體發行者或它的 URL 識別。  如果組件既有強式名稱 \(Strong Name\) 也有軟體發行者識別，那麼會使用軟體發行者識別。  如果組件來自網際網路而且未簽章，則使用 URL 識別。  如需組件和強式名稱的詳細資訊，請參閱[使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)。  
  
-   漫遊存放區與具有漫遊使用者設定檔的使用者一起移動。  檔案將寫入網路目錄，並下載到使用者所登入的任何電腦。  如需漫遊使用者設定檔的詳細資訊，請參閱<xref:System.IO.IsolatedStorage.IsolatedStorageScope?displayProperty=fullName>。  
  
 藉著結合使用者、定義域和組件識別的概念，隔離儲存區可採下列方式隔離資料，每一方式都有各自的使用案例：  
  
-   [依使用者及組件進行隔離](#UserAssembly)  
  
-   [依據使用者、定義域和組件的隔離。](#UserDomainAssembly)  
  
 這些隔離的任一個都可以與漫遊使用者設定檔結合。  如需詳細資訊，請參閱 [隔離儲存區 \(Isolated Storage\) 和 Roaming](#Roaming)。  
  
 下列說明示範存放區如何隔離成不同的範圍。  
  
 ![依據使用者和組件的隔離。](../../../docs/standard/io/media/typesofisolation.gif "typesofisolation")  
隔離儲存區的類型  
  
 注意，除了漫遊存放區以外，隔離儲存區永遠被電腦隱含隔離，因為它使用指定電腦的本機儲存設備。  
  
> [!IMPORTANT]
>  隔離儲存區 \(Isolated Storage\) 是 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式中使用。  相反地，請使用應用程式資料類別在 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 包含的 `Windows.Storage` 命名空間 API 存放區域資料和檔案。  如需詳細資訊， [應用程式資料](http://go.microsoft.com/fwlink/?LinkId=229175) 請參閱 Windows Dev 中心。  
  
<a name="UserAssembly"></a>   
## 依據使用者和組件的隔離  
 當使用資料存放區的組件必須可以從任何應用程式的定義域存取時，依據使用者和組件的隔離是適當的。  基本上，在這個情形中，隔離儲存區被用來儲存資料，且可套用至多個應用程式而且不受任何特定應用程式的限制，例如使用者的名稱或授權資訊。  若要存取使用者和組件所隔離的儲存區，程式碼必須受信任以在應用程式間傳輸資訊。  基本上，依據使用者和組件的隔離在內部網路上被允許，但在網際網路上則否。  呼叫 <xref:System.IO.IsolatedStorage.IsolatedStorageScope?displayProperty=fullName> 的靜態方法並傳入使用者和組件  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 會傳回儲存區，並具隔離性。  
  
 下列程式碼範例擷取使用者和組件所隔離的漫遊存放區。  存放區可以透過 `isoFile`物件來存取。  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 如需使用辨識項 \(Evidence\) 參數的範例，請參閱 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> 方法可當做捷徑使用，如下列程式碼範例所示。  這個捷徑不能用來開啟能夠漫遊的存放區；在此類情況中請使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>。  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## 依據使用者、定義域和組件的隔離  
 如果應用程式使用需要私用 \(Private\) 資料存放區的協力廠商組件，可使用隔離儲存區來儲存私用資料。  依據使用者、定義域和組件的隔離會確保只有指定組件中的程式碼可以存取資料，並且只有當在組件建立存放區時執行的應用程式使用組件時，以及只有當為其建立存放區的使用者執行應用程式時。  依據使用者、定義域和組件的隔離可避免協力廠商組件洩漏資料給其他應用程式。  這個隔離類型應該是您的預設選擇，如果您知道要使用隔離儲存區，但不確定要使哪個隔離類型的話。  呼叫 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 的靜態 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法並傳入使用者、定義域和組件，<xref:System.IO.IsolatedStorage.IsolatedStorageScope> 會傳回這種隔離類型的儲存區。  
  
 下列程式碼範例擷取使用者、定義域和組件所隔離的存放區。  存放區可以透過 `isoFile` 物件來存取。  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 另一個方法可當做捷徑使用，如下列程式碼範例所示。  這個捷徑不能用來開啟能夠漫遊的存放區；在此類情況中請使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>。  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## 隔離儲存區和漫遊  
 漫遊使用者設定檔根據所有個人化設定，可讓使用者將 Web 的識別和使用該識別登入任何網路電腦的 Windows 功能。  使用隔離儲存區的組件可以指定使用者的隔離儲存區要隨著漫遊使用者設定檔移動。  漫遊可以配合使用依據使用者和組件的隔離，或依據使用者、定義域和組件的隔離。  如果不使用漫遊範圍，存放區將不會漫遊，即使使用了漫遊使用者設定檔。  
  
 下列程式碼範例擷取使用者和組件所隔離的漫遊存放區。  存放區可以透過 `isoFile`物件來存取。  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 定義域範圍可被加入以建立使用者、定義域和應用程式所隔離的漫遊存放區。  下列程式碼範例示範這項功能。  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## 請參閱  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>   
 [隔離儲存區](../../../docs/standard/io/isolated-storage.md)