---
title: "建立桌面應用程式的資源檔 | Microsoft Docs"
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
  - ".resources 檔案"
  - "應用程式資源, 建立檔案"
  - "資源檔, .resources 檔案"
  - "資源檔, 建立"
ms.assetid: 6c5ad891-66a0-4e7a-adcf-f41863ba6d8d
caps.latest.revision: 25
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 25
---
# 建立桌面應用程式的資源檔
您可以在資源檔中包含資源 \(例如字串、影像或物件資料\)，輕鬆將其提供給應用程式使用。  .NET Framework 提供五種方式來建立資源檔：  
  
-   建立包含字串資源的文字檔。  您可以使用[資源檔產生器 \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)，將文字檔轉換為二進位資源 \(.resources\) 檔案。  然後您可以使用語言編譯器，將二進位資源檔內嵌在應用程式可執行檔或應用程式庫中，或使用[組件連結器 \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將它內嵌在附屬組件中。  如需詳細資訊，請參閱 [文字檔中的資源](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#TextFiles) 一節。  
  
-   建立包含字串、影像或物件資料的 XML 資源 \(.resx\) 檔案。  您可以使用[資源檔產生器 \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)，將 .resx 檔轉換為二進位資源 \(.resources\) 檔案。  然後您可以使用語言編譯器，將二進位資源檔內嵌在應用程式可執行檔或應用程式庫中，或使用[組件連結器 \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將它內嵌在附屬組件中。  如需詳細資訊，請參閱 [.resx 檔中的資源](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResxFiles)一節。  
  
-   使用 <xref:System.Resources> 命名空間中的型別，以程式設計方式建立 XML 資源 \(.resx\) 檔。  您可以建立 .resx 檔、列舉其資源，然後依名稱擷取特定的資源。  如需詳細資訊，請參閱[以程式設計方式使用 .resx 檔案](../../../docs/framework/resources/working-with-resx-files-programmatically.md)主題。  
  
-   以程式設計方式建立二進位資源 \(.resources\) 檔。  然後您可以使用語言編譯器，將此檔案內嵌在應用程式可執行檔或應用程式庫中，或使用[組件連結器 \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將它內嵌在附屬組件中。  如需詳細資訊，請參閱 [.resources 檔中的資源](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles) 一節。  
  
-   使用 Visual Studio 建立資源檔，並將它併入專案中。  Visual Studio 會提供資源編輯器，讓您加入、刪除及修改資源。  此資源檔在編譯時期會自動轉換成二進位 .resources 檔，並內嵌在應用程式組件或附屬組件中。  如需詳細資訊，請參閱 [Visual Studio 中的資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles) 一節。  
  
<a name="TextFiles"></a>   
## 文字檔中的資源  
 文字 \(.txt\) 檔可用於只儲存字串資源。如果是非字串資源，請使用 .resx 檔案或以程式設計方式加以建立。  包含字串資源的文字檔具有以下格式：  
  
```  
# This is an optional comment.  
name = value  
  
; This is another optional comment.  
name = value  
  
; The following supports conditional compilation if X is defined.  
#ifdef X  
name1=value1  
name2=value2  
#endif  
  
# The following supports conditional compilation if Y is undefined.  
#if !Y  
name1=value1  
name2=value2  
#endif  
  
```  
  
 .txt 或 .restext 檔的資源檔格式完全相同。  .restext 副檔名僅服務可讓文字檔立即可識別為文字基礎的資源檔。  
  
 字串資源會以 *name\/value*組的形式出現，其中 *name*是識別資源的字串，而 *value* 則是當您將 *name* 傳遞給資源擷取方法\(如 <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>\)時所傳回的資源字串。  *name* 和 *value* 必須以等號 \(\=\) 分隔。  例如：  
  
```  
  
FileMenuName=File  
EditMenuName=Edit  
ViewMenuName=View  
HelpMenuName=Help  
  
```  
  
> [!CAUTION]
>  請不要使用資源檔來存放密碼、安全性敏感的資訊或私人資料。  
  
 空字串值 \(也就是 <xref:System.String.Empty?displayProperty=fullName>\) 的資源在文字檔中可以使用。  例如：  
  
```  
EmptyString=  
```  
  
 從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 開始，文字檔支援搭配 `#ifdef` *symbol* 的條件式編譯‧‧‧  `#endif` 和 `#if !`*symbol*‧‧‧  `#endif`建構  您可以使用具有 [資源檔產生器 \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 的 `/define` 參數定義符號。  每個資源要求其自身的 `#ifdef` *symbol*…  `#endif` 或 `#if !`*symbol*‧‧‧  `#endif`建構  如果您使用 `#ifdef` 陳述式及已定義的 *symbol*，相關聯的資源會被包含在 .resources 檔案中；否則它不會被包含。  如果您使用 `#if !` 陳述式及未被定義的 *symbol*，相關聯的資源會被包含在 .resources 檔案中；否則它不會被包含。  
  
 註解在文字檔中為選擇性，而且一行的開頭會有分號 \(;\) 或井字號 \(\#\)。  包含註解的字行可以放在檔案中的任何地方。  註解不會包含在使用[資源檔產生器 \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 建立的已編譯 .resources 檔案中。  
  
 文字檔中的任何空白行都會視為空白字元，並予以忽略。  
  
 下列範例會定義名為 `OKButton` 和 `CancelButton` 的兩個字串資源。  
  
```  
#Define resources for buttons in the user interface.  
OKButton=OK  
CancelButton=Cancel  
```  
  
 如果文字檔包含重複出現的 *name*、[資源檔產生器 \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 會顯示警告，並忽略第二個名稱。  
  
 *value* 不得包含新行字元，但您可以使用類似 `\n` 的 C 程式語言逸出字元代表新行，並以 `\t` 代表跳格。  您也可以包含反斜線字元，如果它逸出 \(例如， "\\ \\ "\)。  此外，允許使用空白字串。  
  
 您可以使用文字檔格式儲存資源，方法是使用位元組由小到大順序或由大到小順序的 UTF\-8 或 UTF\-16 編碼。  但是，將 .txt 檔案轉換成 .resources 檔案的[資源檔產生器 \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 預設會將檔案視為 UTF\-8。  若要讓 Resgen.exe 能辨認使用 UTF\-16 編碼的檔案，請務必在檔案開頭處加入 Unicode 位元組順序標記 \(U\+FEFF\)。  
  
 若要將文字格式的資源檔內嵌在 .NET Framework 組件中，您必須使用[資源檔產生器 \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 將檔案轉換成二進位資源 \(.resources\) 檔案。  然後您可以使用語言編譯器，將 .resources 檔案內嵌在 .NET Framework 組件中，或使用[組件連結器 \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將它內嵌在附屬組件中。  
  
 下列範例會針對簡單的 "Hello World" 主控台應用程式使用文字格式且名為 GreetingResources.txt 的資源檔。  此文字檔會定義兩個字串 `prompt` 和 `greeting`，以提示使用者輸入他的名稱並顯示問候語。  
  
```  
# GreetingResources.txt   
# A resource file in text format for a "Hello World" application.  
#  
# Initial prompt to the user.  
prompt=Enter your name:   
# Format string to display the result.  
greeting=Hello, {0}!  
```  
  
 此文字檔會使用下列命令轉換成 .resources 檔：  
  
 **resgen GreetingResources.txt**  
  
 下列範例會針對使用 .resources 檔顯示訊息給使用者的主控台應用程式來顯示原始程式碼。  
  
 [!code-csharp[Conceptual.Resources.TextFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.textfiles/cs/greeting.cs#1)]
 [!code-vb[Conceptual.Resources.TextFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.textfiles/vb/greeting.vb#1)]  
  
 如果您使用 Visual Basic，而且原始程式碼檔名為 Greeting.vb，則下列命令會建立包含內嵌 .resources 檔的可執行檔：  
  
 **vbc greeting.vb \/resource:GreetingResources.resources**  
  
 如果您使用 C\#，而且原始程式碼檔名為 Greeting.cs，則下列命令會建立包含內嵌 .resources 檔的可執行檔：  
  
 **csc greeting.cs \/resource:GreetingResources.resources**  
  
<a name="ResxFiles"></a>   
## .resx 檔中的資源  
 不像只能儲存字串資源的文字檔，XML 資源 \(.resx\) 檔可以儲存字串、二進位資料 \(如影像、圖示和音訊剪輯\) 及程式設計物件。  .resx 檔包含標準標頭，此標頭可描述資源項目的格式，並指定用來剖析資料之 XML 的版本資訊。  在 XML 標頭後面的資源檔資料。  每一個資料項目都是由 `data` 標籤內所包含的名稱\/值組所組成。  它的 `name` 屬性會定義資源名稱，而巢狀 `value` 標籤則包含資源值。  如果是字串資料，`value` 標籤會包含字串。  
  
 例如，下列 `data` 標籤會定義名為 `prompt` 的字串資源，其值為 "Enter your name:"。  
  
```  
<data name="prompt" xml:space="preserve">  
  <value>Enter your name:</value>  
</data>  
```  
  
> [!WARNING]
>  請不要使用資源檔來存放密碼、安全性敏感的資訊或私人資料。  
  
 如果是資源物件，**data** 標籤會包含指示資源資料型別的 `type` 屬性。  如果是由二進位資料組成的物件，`data` 標籤也會包含 `mimetype` 屬性，該屬性會指示二進位資料的 `base64` 型別。  
  
> [!NOTE]
>  所有 .resx 檔案都使用二進位序列化格式子 \(Serialization Formatter\) 產生並剖析特定型別的二進位資料。  因此，如果某物件的二進位序列化格式以不相容的方式變更，.resx 檔會變為無效。  
  
 下列範例顯示 .resx 檔的一部分，其中包含 <xref:System.Int32> 資源和點陣圖影像。  
  
```  
  
<data name="i1" type="System.Int32, mscorlib">  
  <value>20</value>  
</data>  
  
<data name="flag" type="System.Drawing.Bitmap, System.Drawing,     
    Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"   
    mimetype="application/x-microsoft.net.object.bytearray.base64">  
  <value>  
    AAEAAAD/////AQAAAAAAAAAMAgAAADtTeX…  
  </value>  
</data>  
```  
  
> [!IMPORTANT]
>  因為 .resx 檔案必須由預先定義格式且語式正確的 XML 所組成，所以我們不建議您手動處理 .resx 檔案，特別是當 .resx 檔案包含字串以外的資源時。  反之，Visual Studio 提供透明的介面來建立及操作 .resx 檔。如需詳細資訊，請參閱 [Visual Studio 中的資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles) 章節。  您也可以程式設計方式建立及操作 .resx 檔案。  如需詳細資訊，請參閱[以程式設計方式使用 .resx 檔案](../../../docs/framework/resources/working-with-resx-files-programmatically.md)。  
  
<a name="ResourcesFiles"></a>   
## .resources 檔中的資源  
 您可以使用 <xref:System.Resources.ResourceWriter?displayProperty=fullName> 類別，以程式設計方式直接從程式碼建立二進位資源 \(.resources\) 檔。  您也可以使用[資源檔產生器 \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)，從文字檔或 .resx 檔建立 .resources 檔。  .resources 檔除了字串資料以外，還可包含二進位資料 \(位元組陣列\) 和物件資料。  以程式設計方式建立 .resources 檔需要下列步驟：  
  
1.  建立具有唯一檔案名稱的 <xref:System.Resources.ResourceWriter> 物件。  若要這樣做，請針對 <xref:System.Resources.ResourceWriter> 類別建構函式指定檔案名稱或檔案資料流。  
  
2.  針對您要加入至檔案中的每一項具名資源呼叫 <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=fullName> 方法的其中一個多載。  資源可以是字串、物件或二進位資料的集合 \(位元組陣列\)。  
  
3.  呼叫 <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=fullName> 方法可將資源寫入檔案中並關閉 <xref:System.Resources.ResourceWriter> 物件。  
  
> [!NOTE]
>  請不要使用資源檔來存放密碼、安全性敏感的資訊或私人資料。  
  
 下列範例會以程式設計方式建立名為 CarResources.resources 的 .resources 檔案，該檔案會儲存六個字串、一個圖示和兩個應用程式定義的物件 \(兩個 `Automobile` 物件\)。  請注意，此範例中所定義及具現化的 `Automobile` 類別會以 <xref:System.SerializableAttribute> 屬性標記，好讓二進位序列化格式器得以保存它。  
  
 [!code-csharp[Conceptual.Resources.Resources#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resources/cs/resources1.cs#1)]
 [!code-vb[Conceptual.Resources.Resources#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resources/vb/resources1.vb#1)]  
  
 在您建立 .resources 檔之後，您可以藉由包含語言編譯器的 `/resource` 參數將它內嵌在執行階段可執行檔或程式庫中，或使用[組件連結器 \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將它內嵌在附屬組件中。  
  
<a name="VSResFiles"></a>   
## Visual Studio 中的資源檔  
 當您將資源檔加入至 Visual Studio 專案時，Visual Studio 會在專案目錄中建立 .resx 檔。  Visual Studio 會提供資源編輯器，好讓您加入字串、影像和二進位物件。  因為編輯器的設計目的只是為了處理靜態資料，所以不能用來儲存程式設計物件。您必須以程式設計方式將物件資料寫入 .resx 檔或 .resources 檔。  請參閱 [以程式設計方式使用 .resx 檔案](../../../docs/framework/resources/working-with-resx-files-programmatically.md) 主題和 [.resources 檔中的資源](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles) 章節以取得詳細資訊。  
  
 如果您要加入當地語系化資源，您應該為其提供與主要資源檔相同的根檔案名稱，而且您也應該在檔案名稱中指定其文化特性。  例如，如果您加入名為 Resources.resx 的資源檔，您可能也會建立名為 Resources.en\-US.resx 和 Resources.fr\-FR.resx 的資源檔，以分別保存英文 \(美國\) 和法文 \(法國\) 文化特性的當地語系化資源。  您也應該指定應用程式的預設文化特性。  當找不到特定文化特性的當地語系化資源時，就會使用此文化特性的資源。  若要指定預設文化特性，請在 Visual Studio 的 \[方案總管\] 中以滑鼠右鍵按一下專案名稱、指向 \[應用程式\]、按一下 \[**組件資訊**\]，並在 \[**中性語言**\] 清單中選取適當的語言\/文化特性。  
  
 Visual Studio 在編譯時期會先將專案中的 .resx 檔轉換成二進位資源 \(.resources\) 檔，並將其儲存在專案 obj 目錄的子目錄中。  Visual Studio 會將未包含當地語系化資源的任何資源檔內嵌在專案所產生的主要組件中。  如果有任何資源檔包含當地語系化資源，Visual Studio 會將其內嵌在每一個當地語系化文化特性的個別附屬組件中。  然後它會將每一個附屬組件儲存在名稱與當地語系化文化特性對應的目錄中。  例如，當地語系化英文 \(美國\) 資源會儲存在附屬組件的 en\-US 子目錄中。  
  
## 請參閱  
 <xref:System.Resources>   
 [桌面應用程式中的資源](../../../docs/framework/resources/index.md)   
 [封裝和部署資源](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)