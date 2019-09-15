---
title: 建立桌面應用程式的附屬組件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- public keys, obtaining
- satellite assemblies
- assemblies [.NET Framework], signing
- application resources, deploying
- Al.exe
- GAC (global assembly cache), satellite assemblies
- Assembly Linker
- directory locations for satellite assemblies
- global assembly cache, satellite assemblies
- packaging application resources
- compiling satellite assemblies
- re-signing assemblies
ms.assetid: 8d5c6044-2919-41d2-8321-274706b295ac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29739625d29db6dc7c3876007f1e733b15f5c026
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970983"
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a>建立桌面應用程式的附屬組件

資源檔在當地語系化的應用程式中扮演重要角色。 它們可讓應用程式以使用者自己的語言和文化特性顯示字串、影像和其他資料，以及在使用者自己的語言或文化特性的資源無法使用時提供替代資料。 .NET Framework 會使用中樞和支點模型來尋找並擷取當地語系化的資源。 中樞是主要組件，其中包含未當地語系化的可執行程式碼以及稱為中性或預設文化特性之單一文化特性的資源。 預設文化特性是應用程式的後援文化特性；當地語系化的資源無法使用時會使用它。 您使用 <xref:System.Resources.NeutralResourcesLanguageAttribute> 屬性來指定應用程式之預設文化特性的文化特性。 每個支點都會連線至附屬組件，其中包含單一當地語系化文化特性但未包含任何程式碼的資源。 因為附屬組件不是主要組件的一部分，所以您可以輕鬆地更新或取代對應至特定文化特性的資源，而不需要取代應用程式的主要組件。

> [!NOTE]
> 應用程式之預設文化特性的資源也可以儲存在附屬組件中。 若要這樣做，請將 <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> 的值指派給 <xref:System.Resources.NeutralResourcesLanguageAttribute> 屬性。

## <a name="satellite-assembly-name-and-location"></a>附屬組件名稱和位置

中樞和支點模型需要您將資源放入特定位置，以輕鬆地找到和使用它們。 如果您未如預期編譯和命名資源，或未將它們放在正確位置，則 Common Language Runtime 會找不到它們，並改為使用預設文化特性的資源。 以 <xref:System.Resources.ResourceManager> 物件代表的 .NET Framework Resource Manager 是用來自動存取當地語系化資源。 Resource Manager 需要下列各項：

- 單一附屬組件必須包括特定文化特性的所有資源。 換句話說，您應該將多個 .txt 或 .resx 檔案編譯成單一二進位 .resources 檔案。

- 在儲存該文化特性資源之每個當地語系化文化特性的應用程式目錄中，都必須有不同的子目錄。 子目錄名稱必須與文化特性名稱相同。 或者，您可以在全域組件快取中儲存附屬組件。 在此情況下，組件強式名稱的文化特性資訊元件必須指出其文化特性。 (請參閱本主題稍後的[在全域組件快取中安裝附屬組件](#SN)一節)。

  > [!NOTE]
  > 如果您的應用程式包括子文化特性的資源，請將每個子文化特性放在應用程式目錄下的不同子目錄中。 請不要將子文化特性放在其主要文化特性目錄的子目錄中。

- 附屬組件的名稱必須與應用程式相同，而且必須使用副檔名 ".resources.dll"。 例如，如果應用程式命名為 Example.exe，則每個附屬組件的名稱應該是 Example.resources.dll。 請注意，附屬組件名稱不會指出其資源檔的文化特性。 不過，附屬組件會出現在確實指定文化特性的目錄中。

- 附屬組件文化特性的資訊必須包括在組件的中繼資料內。 若要將文化特性名稱儲存在附屬組件的中繼資料內，請在使用[組件連結器](../tools/al-exe-assembly-linker.md)將資源內嵌在附屬組件時指定 `/culture` 選項。

下圖顯示未在[全域組件快取](../../framework/app-domains/gac.md)中安裝之應用程式的範例目錄結構和位置需求。 副檔名為 .txt 和 .resources 的項目將不會隨附最終應用程式。 這些是用來建立最終附屬資源組件的中繼資源檔。 在此範例中，您可以將 .resx 檔案取代為 .txt 檔案。 如需詳細資訊，請參閱[封裝和部署資源](packaging-and-deploying-resources-in-desktop-apps.md)。

下圖顯示附屬組件目錄：

![使用當地語系化文化特性 (Culture) 子目錄的附屬組件目錄。](./media/creating-satellite-assemblies-for-desktop-apps/satellite-assembly-directory.gif)

## <a name="compiling-satellite-assemblies"></a>編譯附屬組件

您使用[資源檔產生器 (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md)，將包含資源的文字檔或 XML (.resx) 檔案編譯成二進位 .resources 檔案。 您接著使用[組件連結器 (Al.exe)](../tools/al-exe-assembly-linker.md) 將 .resources 檔案編譯成附屬組件。 Al.exe 會從您指定的 .resources 檔案建立組件。 附屬組件只能包含資源，而不能包含任何可執行程式碼。

下列 Al.exe 命令會從德文資源檔 strings.de.resources 建立應用程式 `Example` 的附屬組件。

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll
```

下列 Al.exe 命令也會從 strings.de.resources 檔案建立應用程式 `Example` 的附屬組件。 **/template** 選項會讓附屬組件從父組件 (Example.dll) 繼承所有組件中繼資料，但其文化特性資訊除外。

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll
```  
  
 下表更詳細描述在這些命令中使用的 Al.exe 選項。
  
|選項|描述|
|------------|-----------------|
|**-target:** lib|指定將附屬組件編譯成程式庫 (.dll) 檔案。 因為附屬組件未包含可執行程式碼，而且不是應用程式的主要組件，所以您必須將附屬組件儲存為 DLL。|
|**-embed:** strings.de.resources|指定要在 Al.exe 編譯組件時內嵌的資源檔名稱。 您可以在附屬組件中內嵌多個 .resources 檔案；但是，如果您遵循中樞和支點模型，則必須為每個文化特性編譯一個附屬組件。 不過，您可以為字串和物件建立個別的 .resources 檔案。|
|**-culture:** de|指定要編譯之資源的文化特性。 Common Language Runtime 在搜尋所指定文化特性的資源時會使用這項資訊。 如果您省略這個選項，Al.exe 還是會編譯資源，但執行階段在使用者要求資源時會找不到。|
|**-out:** Example.resources.dll|指定輸出檔案的名稱。 名稱必須遵循命名標準 <基底名稱>.resources.<副檔名>，其中 <基底名稱> 為主要組件的名稱，<副檔名> 則為有效的副檔名 (例如 .dll)。 請注意，執行階段無法根據輸出檔名稱來判斷附屬組件的文化特性；您必須使用 **/culture** 選項來指定它。|
|**-template:** Example.dll|指定附屬組件要從中繼承所有組件中繼資料的組件，但不包括文化特性欄位。 只有在您指定的組件具有[強式名稱](../../standard/assembly/strong-named.md)時，此選項才會影響附屬組件。|
  
 如需 Al.exe 的完整可用選項清單，請參閱[組件連結器 (Al.exe)](../tools/al-exe-assembly-linker.md)。
  
## <a name="satellite-assemblies-an-example"></a>附屬組件：範例  
 下列簡單 "Hello world" 範例會顯示包含當地語系化問候語的訊息方塊。 此範例包括英文 (美國)、法文 (法國) 和俄文 (俄國) 文化特性的資源，而其後援文化特性是英文。 若要建立範例，請執行下列動作：  
  
1. 建立名為 Greeting.resx 或 Greeting.txt 的資源檔，以包含預設文化特性的資源。 將名為 `HelloString` 且其值為 "Hello world!" 的單一字串儲存 在此檔案中。
  
2. 若要指出英文 (en) 是應用程式的預設文化特性，請將下列 <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> 屬性新增至應用程式的 AssemblyInfo 檔案或將編譯為應用程式主要組件的主要原始程式碼檔案。
  
     [!code-csharp[Conceptual.Resources.Locating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
     [!code-vb[Conceptual.Resources.Locating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3. 將其他文化特性 (en-US、fr-FR 和 ru-RU) 的支援新增至應用程式，如下所示：  
  
    - 若要支援 en-US 或英文 (美國) 文化特性，請建立名為 Greeting.en-US.resx 或 Greeting.en-US.txt 的資源檔，並在其中儲存名為 `HelloString` 且其值為 "Hi world!" 的單一字串。  
  
    - 若要支援 fr-FR 或法文 (法國) 文化特性，請建立名為 Greeting.fr-FR.resx 或 Greeting.fr-FR.txt 的資源檔，並在其中儲存名為 `HelloString` 且其值為 "Salut tout le monde!" 的單一字串。  
  
    - 若要支援 ru-RU 或俄文 (俄國) 文化特性，請建立名為 Greeting.ru-RU.resx 或 Greeting.ru-RU.txt 的資源檔，並在其中儲存名為 `HelloString` 且其值為 "Всем привет!" 的單一字串。  
  
4. 使用 [Resgen.exe](../tools/resgen-exe-resource-file-generator.md)，將每一個文字或 XML 資源檔編譯成二進位 .resources 檔案。 輸出是根檔案名稱與 .resx 或 .txt 檔案相同的一組檔案，但副檔名為 .resources。 如果您使用 Visual Studio 建立範例，則會自動處理編譯程序。 如果您不要使用 Visual Studio，請執行下列命令將 .resx 檔案編譯為 .resources 檔案：  
  
    ```console
    resgen Greeting.resx
    resgen Greeting.en-us.resx
    resgen Greeting.fr-FR.resx
    resgen Greeting.ru-RU.resx
    ```

    如果您的資源是文字檔，而非 XML 檔案，請將副檔名 .resx 取代為 .txt。

5. 將下列原始程式碼與預設文化特性的資源編譯為應用程式的主要組件：

    > [!IMPORTANT]
    > 如果您使用命令列建立範例而非 Visual Studio，則應該將 <xref:System.Resources.ResourceManager> 類別建構函式的呼叫修改為下列：`ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`

    [!code-csharp[Conceptual.Resources.Locating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
    [!code-vb[Conceptual.Resources.Locating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]

    如果應用程式命名為 Example，而且您從命令列進行編譯，則 C# 編譯器的命令是：

    ```console
    csc Example.cs -res:Greeting.resources
    ```

    對應的 Visual Basic 編譯器命令為：

    ```console
    vbc Example.vb -res:Greeting.resources
    ```

6. 在應用程式所支援之每個當地語系化文化特性的主要應用程式目錄中，建立子目錄。 您應該建立 en-US、fr-FR 和 ru-RU 子目錄。 Visual Studio 會在編譯程序時自動建立這些子目錄。

7. 將個別文化特性特定 .resources 檔案內嵌到附屬組件，並將它們儲存到適當的目錄。 針對每個 .resources 檔案執行這項作業的命令為：

    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll
    ```  
  
     其中 *culture* 是附屬組件會包含其資源的文化特性名稱。 Visual Studio 會自動處理這個程序。
  
 您接著可以執行此範例。 它會隨機讓其中一個支援的文化特性成為目前文化特性，並顯示當地語系化的問候語。
  
<a name="SN"></a>   
## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a>在全域組件快取中安裝附屬組件  
 您可以將組件安裝在全域組件快取中，而不是在本機應用程式子目錄中安裝組件。 如果您有供多個應用程式使用的類別庫和類別庫資源組件，則這特別有用。
  
 在全域組件快取中安裝組件時，需要組件具有強式名稱。 強式名稱組件會使用有效的公開/私密金鑰組進行簽署。 它們包含執行階段用來判斷要用來滿足繫結要求之組件的版本資訊。 如需強式名稱和版本控制的詳細資訊，請參閱[組件版本控制](../../standard/assembly/versioning.md)。 如需強式名稱的詳細資訊，請參閱[強式名稱的組件](../../standard/assembly/strong-named.md)。
  
 當您開發應用程式時，可能無法存取最終公開/私密金鑰組。 若要在全域組件快取中安裝附屬組件，並確認它的運作正常，您可以使用稱為延遲簽署的技術。 當您延遲簽署組件時，請在建置時間於檔案中保留強式名稱簽章的空間。 有最終公開/私密金鑰組可用時，會將實際簽署延遲到稍後。 如需延遲簽署的詳細資訊，請參閱[延遲簽署組件](../../standard/assembly/delay-sign.md)。
  
### <a name="obtaining-the-public-key"></a>取得公開金鑰  
 若要延遲簽署組件，您必須具有公開金鑰的存取權。 您可以從公司中進行最後簽署的組織中取得實際公開金鑰，或使用[強式名稱工具 (Sn.exe)](../tools/sn-exe-strong-name-tool.md) 建立公開金鑰。
  
 下列 Sn.exe 命令會建立測試公開/私密金鑰組。 **–k** 選項會指定 Sn.exe 應該建立新的金鑰組，並將它儲存在名為 TestKeyPair.snk 的檔案中。
  
```console
sn –k TestKeyPair.snk
```

您可以從包含測試金鑰組的檔案中擷取公開金鑰。 下列命令會從 TestKeyPair.snk 擷取公開金鑰，並將它儲存在 PublicKey.snk 中：

```console
sn –p TestKeyPair.snk PublicKey.snk
```

### <a name="delay-signing-an-assembly"></a>延遲簽署組件

在您取得或建立公開金鑰之後，請使用[組件連結器 (Al.exe)](../tools/al-exe-assembly-linker.md) 編譯組件，並指定延遲簽署。

下列 Al.exe 命令會從 strings.ja.resources 檔案建立應用程式 StringLibrary 的強式名稱附屬組件：

```console
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk
```

選項指定組件連結器應該延遲簽署組件。 **-keyfile** 選項指定金鑰檔名稱，其中包含要用來延遲簽署組件的公開金鑰。

### <a name="re-signing-an-assembly"></a>重新簽署組件

部署您的應用程式之前，必須使用實際金鑰組來重新簽署延遲簽署的附屬組件。 您可以使用 Sn.exe 完成這項動作。

下列 Sn.exe 命令會使用 RealKeyPair.snk 檔案中所儲存的金鑰組來簽署 StringLibrary.resources.dll。 **–R** 選項指定要重新簽署先前簽署的組件還是延遲簽署的組件。

```console
sn –R StringLibrary.resources.dll RealKeyPair.snk
```

### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a>在全域組件快取中安裝附屬組件

執行階段在資源後援程序中搜尋資源時，會先尋找[全域組件快取](../../framework/app-domains/gac.md) (如需詳細資訊，請參閱[封裝和部署資源](packaging-and-deploying-resources-in-desktop-apps.md)主題的＜資源後援程序＞一節)。只要附屬組件是使用強式名稱進行簽署，就可以使用[全域組件快取工具 (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) 將它安裝在全域組件快取中。

下列 Gacutil.exe 命令會在全域組件快取中安裝 StringLibrary.resources.dll：

```console
gacutil -i:StringLibrary.resources.dll
```

**/i** 選項指定 Gacutil.exe 應該將指定的組件安裝到全域組件快取。 在快取中安裝附屬組件之後，其所含的資源可供設計成使用附屬組件的所有應用程式使用。

### <a name="resources-in-the-global-assembly-cache-an-example"></a>全域組件快取中的資源：範例

下列範例會使用 .NET Framework 類別庫中的方法，從資源檔擷取並傳回當地語系化的問候。 程式庫和其資源都會註冊在全域組件快取中。 此範例包括英文 (美國)、法文 (法國)、俄文 (俄國) 和英文文化特性的資源。 英文是預設文化特性；其資源儲存在主要組件中。 此範例一開始會使用公開金鑰來延遲簽署程式庫和其附屬組件，然後使用公開/私密金鑰組來重新簽署它們。 若要建立範例，請執行下列動作：

1. 如果您未使用 Visual Studio，請使用下列[強式名稱工具 (Sn.exe)](../tools/sn-exe-strong-name-tool.md) 命令來建立名為 ResKey.snk 的公開/私密金鑰組：

    ```console
    sn –k ResKey.snk
    ```

    如果您使用 Visual Studio，請使用專案 [屬性] 對話方塊的 [簽署] 索引標籤來產生金鑰檔。

2. 使用下列[強式名稱工具 (Sn.exe)](../tools/sn-exe-strong-name-tool.md) 命令來建立名為 PublicKey.snk 的公用金鑰檔案：

    ```console
    sn –p ResKey.snk PublicKey.snk
    ```

3. 建立名為 Strings.resx 的資源檔，以包含預設文化特性的資源。 將名為 `Greeting` 且其值為 "How do you do?" 的單一字串儲存 在該檔案中。

4. 若要指出 "en" 是應用程式的預設文化特性，請將下列 <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> 屬性新增至應用程式的 AssemblyInfo 檔案或將編譯為應用程式主要組件的主要原始程式碼檔案：

    [!code-csharp[Conceptual.Resources.Satellites#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
    [!code-vb[Conceptual.Resources.Satellites#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]

5. 將其他文化特性 (en-US、fr-FR 和 ru-RU 文化特性) 的支援新增至應用程式，如下所示：

    - 若要支援 "en-US" 或英文 (美國) 文化特性，請建立名為 Strings.en-US.resx 或 Strings.en-US.txt 的資源檔，並在其中儲存名為 `Greeting` 且其值為 "Hello!" 的單一字串。

    - 若要支援 "fr-FR" 或法文 (法國) 文化特性，請建立名為 Strings.fr-FR.resx 或 Strings.fr-FR.txt 的資源檔，並在其中儲存名為 `Greeting` 且其值為 "Bon jour!" 的單一字串。

    - 若要支援 "ru-RU" 或俄文 (俄國) 文化特性，請建立名為 Strings.ru-RU.resx 或 Strings.ru-RU.txt 的資源檔，並在其中儲存名為 `Greeting` 且其值為 "Привет!" 的單一字串。

6. 使用 [Resgen.exe](../tools/resgen-exe-resource-file-generator.md)，將每一個文字或 XML 資源檔編譯成二進位 .resources 檔案。 輸出是根檔案名稱與 .resx 或 .txt 檔案相同的一組檔案，但副檔名為 .resources。 如果您使用 Visual Studio 建立範例，則會自動處理編譯程序。 如果您不要使用 Visual Studio，請執行下列命令將 .resx 檔案編譯為 .resources 檔案：

    ```console
    resgen filename
    ```

    其中 <檔案名稱> 是 .resx 或文字檔的選擇性路徑、檔案名稱和副檔名。

7. 將 StringLibrary.vb 或 StringLibrary.cs 的下列原始程式碼以及預設文化特性的資源編譯為名為 StringLibrary.dll 的延遲簽署程式庫組件：

    > [!IMPORTANT]
    > 如果您使用命令列而非 Visual Studio 來建立範例，則應該將 <xref:System.Resources.ResourceManager> 類別建構函式的呼叫修改為 `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`。

    [!code-csharp[Conceptual.Resources.Satellites#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
    [!code-vb[Conceptual.Resources.Satellites#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]

    C# 編譯器的命令是：

    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs
    ```

    對應的 Visual Basic 編譯器命令為：

    ```console
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb
    ```

8. 在應用程式所支援之每個當地語系化文化特性的主要應用程式目錄中，建立子目錄。 您應該建立 en-US、fr-FR 和 ru-RU 子目錄。 Visual Studio 會在編譯程序時自動建立這些子目錄。 因為所有附屬組件都有相同的檔案名稱，所以使用子目錄來儲存個別文化特性特定附屬組件，直到使用公開/私密金鑰組簽署它們為止。

9. 將個別文化特性特定 .resources 檔案內嵌到延遲簽署的附屬組件，並將它們儲存到適當的目錄。 針對每個 .resources 檔案執行這項作業的命令為：

    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk
    ```

    其中 *culture* 是文化特性的名稱。 在此範例中，文化特性名稱是 en-US、fr-FR 和 ru-RU。

10. 使用[強式名稱工具 (Sn.exe)](../tools/sn-exe-strong-name-tool.md) 來重新簽署 StringLibrary.dll，如下所示：

    ```console
    sn –R StringLibrary.dll RealKeyPair.snk
    ```

11. 重新簽署個別附屬組件。 若要這樣做，請使用每個附屬組件的[強式名稱工具 (Sn.exe)](../tools/sn-exe-strong-name-tool.md)，如下所示：

    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk
    ```

12. 使用下列命令，在全域組件快取中註冊 StringLibrary.dll 和其每個附屬組件：

    ```console
    gacutil -i filename
    ```

    其中 <檔案名稱> 是要註冊之檔案的名稱。

13. 如果您使用 Visual Studio，請建立名為 `Example` 的新**主控台應用程式**專案，並在其中新增 StringLibrary.dll 參考和下列原始程式碼，然後進行編譯。

    [!code-csharp[Conceptual.Resources.Satellites#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
    [!code-vb[Conceptual.Resources.Satellites#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]

    若要從命令列進行編譯，請針對 C# 編譯器使用下列命令：

    ```console
    csc Example.cs -r:StringLibrary.dll
    ```

    Visual Basic 編譯器的命令列為：

    ```console
    vbc Example.vb -r:StringLibrary.dll
    ```

14. 執行 Example.exe。

## <a name="see-also"></a>另請參閱

- [封裝和部署資源](packaging-and-deploying-resources-in-desktop-apps.md)
- [延遲簽署組件](../../standard/assembly/delay-sign.md)
- [Al.exe (組件連結器)](../tools/al-exe-assembly-linker.md)
- [Sn.exe (強式名稱工具)](../tools/sn-exe-strong-name-tool.md)
- [Gacutil.exe (全域組件快取工具)](../tools/gacutil-exe-gac-tool.md)
- [桌面應用程式中的資源](index.md)
