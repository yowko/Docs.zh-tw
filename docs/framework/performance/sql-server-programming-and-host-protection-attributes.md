---
title: "SQL Server 程式設計和主機保護屬性 | Microsoft Docs"
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
  - "主應用程式保護屬性"
  - "HostProtectionAttribute 類別, 可靠性"
  - "主應用程式, 可靠性"
  - "Managed 程式碼, SQL Server"
  - "使用權限集合, SQL Server"
  - "可靠性 [.NET Framework]"
  - "SQL Server [.NET Framework]"
  - "SQL Server 程式設計和主機保護屬性"
  - "編寫可靠的程式碼"
ms.assetid: 7dfa36b4-e773-4c75-a3ff-ff1af3ce4c4f
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# SQL Server 程式設計和主機保護屬性
在 SQL Server 主應用程式中載入及執行 Managed 程式碼的能力，需要符合主應用程式對於程式碼存取安全性和主應用程式資源保護的需求。程式碼存取安全性的需求是由下列三個 SQL Server 使用權限集合的其中一個所指定：SAFE、EXTERNAL\-ACCESS 或 UNSAFE。  在 SAFE 或 EXTERNAL\-ACCESS 使用權限集合內執行的程式碼，必須避免某些已套用 <xref:System.Security.Permissions.HostProtectionAttribute> 屬性的型別或成員。  <xref:System.Security.Permissions.HostProtectionAttribute> 並不是和可靠性保證同等的安全性權限，因為它會識別主應用程式可能不允許的特定程式碼建構 \(型別或方法\)。使用 <xref:System.Security.Permissions.HostProtectionAttribute> 會強制使用有助於保護主應用程式之穩定性的程式設計模型。  
  
## 主應用程式保護屬性  
 主應用程式保護屬性可識別不適合主應用程式設計模型以及表示下列可靠性威脅等級提高的型別或成員：  
  
-   否則為良性。  
  
-   可能會導致受伺服器管理之使用者程式碼不穩定。  
  
-   可能會導致伺服器處理序本身的不穩定。  
  
 SQL Server 不允許使用具有 <xref:System.Security.Permissions.HostProtectionAttribute> \(會指定 <xref:System.Security.Permissions.HostProtectionResource>、<xref:System.Security.Permissions.HostProtectionResource>、<xref:System.Security.Permissions.HostProtectionResource> 或 <xref:System.Security.Permissions.HostProtectionResource> 的 <xref:System.Security.Permissions.HostProtectionResource> 值\) 的型別或成員。  這會讓組件無法呼叫啟用共用狀態、執行同步處理、在終止時可能造成資源流失、或是會影響 SQL Server 處理序完整性的成員。  
  
### 不允許的型別和成員  
 下表將識別一些型別和成員，SQL Server 不允許使用它們的 <xref:System.Security.Permissions.HostProtectionResource> 值。  
  
|命名空間|型別或成員|  
|----------|-----------|  
|`Microsoft.Win32`|<xref:Microsoft.Win32.PowerModeChangedEventArgs> 類別<br /><br /> <xref:Microsoft.Win32.PowerModeChangedEventHandler> 委派<br /><br /> <xref:Microsoft.Win32.SessionEndedEventArgs> 類別<br /><br /> <xref:Microsoft.Win32.SessionEndedEventHandler> 委派<br /><br /> <xref:Microsoft.Win32.SessionEndingEventArgs> 類別<br /><br /> <xref:Microsoft.Win32.SessionEndingEventHandler> 委派<br /><br /> <xref:Microsoft.Win32.SessionSwitchEventArgs> 類別<br /><br /> <xref:Microsoft.Win32.SessionSwitchEventHandler> 委派<br /><br /> <xref:Microsoft.Win32.SystemEvents> 類別<br /><br /> <xref:Microsoft.Win32.TimerElapsedEventArgs> 類別<br /><br /> <xref:Microsoft.Win32.TimerElapsedEventHandler> 委派<br /><br /> <xref:Microsoft.Win32.UserPreferenceChangedEventArgs> 類別<br /><br /> <xref:Microsoft.Win32.UserPreferenceChangingEventArgs> 類別|  
|`System.Collections`|<xref:System.Collections.ArrayList.Synchronized%2A?displayProperty=fullName> 方法<br /><br /> <xref:System.Collections.Hashtable.Synchronized%2A?displayProperty=fullName> 方法<br /><br /> <xref:System.Collections.Queue.Synchronized%2A?displayProperty=fullName> 方法<br /><br /> <xref:System.Collections.SortedList.Synchronized%2A?displayProperty=fullName> 方法<br /><br /> <xref:System.Collections.Stack.Synchronized%2A?displayProperty=fullName> 方法|  
|`System.ComponentModel`|<xref:System.ComponentModel.AddingNewEventArgs> 類別<br /><br /> <xref:System.ComponentModel.AddingNewEventHandler> 委派<br /><br /> <xref:System.ComponentModel.ArrayConverter> 類別<br /><br /> <xref:System.ComponentModel.AsyncCompletedEventArgs> 類別<br /><br /> <xref:System.ComponentModel.AsyncCompletedEventHandler> 委派<br /><br /> <xref:System.ComponentModel.AsyncOperation> 類別<br /><br /> <xref:System.ComponentModel.AsyncOperationManager> 類別<br /><br /> <xref:System.ComponentModel.AttributeCollection> 類別<br /><br /> <xref:System.ComponentModel.BackgroundWorker> 類別<br /><br /> <xref:System.ComponentModel.BaseNumberConverter> 類別<br /><br /> <xref:System.ComponentModel.BindingList%601> 類別<br /><br /> <xref:System.ComponentModel.BooleanConverter> 類別<br /><br /> <xref:System.ComponentModel.ByteConverter> 類別<br /><br /> <xref:System.ComponentModel.CancelEventArgs> 類別<br /><br /> <xref:System.ComponentModel.CancelEventHandler> 委派<br /><br /> <xref:System.ComponentModel.CharConverter> 類別<br /><br /> <xref:System.ComponentModel.CollectionChangeEventArgs> 類別<br /><br /> <xref:System.ComponentModel.CollectionChangeEventHandler> 委派<br /><br /> <xref:System.ComponentModel.CollectionConverter> 類別<br /><br /> <xref:System.ComponentModel.ComponentCollection> 類別<br /><br /> <xref:System.ComponentModel.ComponentConverter> 類別<br /><br /> <xref:System.ComponentModel.ComponentEditor> 類別<br /><br /> <xref:System.ComponentModel.ComponentResourceManager> 類別<br /><br /> <xref:System.ComponentModel.Container> 類別<br /><br /> <xref:System.ComponentModel.ContainerFilterService> 類別<br /><br /> <xref:System.ComponentModel.CultureInfoConverter> 類別<br /><br /> <xref:System.ComponentModel.CustomTypeDescriptor> 類別<br /><br /> <xref:System.ComponentModel.DateTimeConverter> 類別<br /><br /> <xref:System.ComponentModel.DecimalConverter> 類別<br /><br /> <xref:System.ComponentModel.Design.ActiveDesignerEventArgs> 類別<br /><br /> <xref:System.ComponentModel.Design.ActiveDesignerEventHandler> 委派<br /><br /> <xref:System.ComponentModel.Design.CheckoutException> 類別<br /><br /> <xref:System.ComponentModel.Design.CommandID> 類別<br /><br /> <xref:System.ComponentModel.Design.ComponentChangedEventArgs> 類別<br /><br /> <xref:System.ComponentModel.Design.ComponentChangedEventHandler> 委派<br /><br /> <xref:System.ComponentModel.Design.ComponentChangingEventArgs> 類別<br /><br /> <xref:System.ComponentModel.Design.ComponentChangingEventHandler> 委派<br /><br /> <xref:System.ComponentModel.Design.ComponentEventArgs> 類別<br /><br /> <xref:System.ComponentModel.Design.ComponentEventHandler> 委派<br /><br /> <xref:System.ComponentModel.Design.ComponentRenameEventArgs> 類別<br /><br /> <xref:System.ComponentModel.Design.ComponentRenameEventHandler> 委派<br /><br /> <xref:System.ComponentModel.Design.DesignerCollection> 類別<br /><br /> <xref:System.ComponentModel.Design.DesignerEventArgs> 類別<br /><br /> <xref:System.ComponentModel.Design.DesignerEventHandler> 委派<br /><br /> <xref:System.ComponentModel.Design.DesignerOptionService> 類別<br /><br /> <xref:System.ComponentModel.Design.DesignerTransaction> 類別<br /><br /> <xref:System.ComponentModel.Design.DesignerTransactionCloseEventArgs> 類別<br /><br /> <xref:System.ComponentModel.Design.DesignerTransactionCloseEventHandler> 委派<br /><br /> <xref:System.ComponentModel.Design.DesignerVerb> 類別<br /><br /> <xref:System.ComponentModel.Design.DesignerVerbCollection> 類別<br /><br /> <xref:System.ComponentModel.Design.DesigntimeLicenseContext> 類別<br /><br /> <xref:System.ComponentModel.Design.DesigntimeLicenseContextSerializer> 類別<br /><br /> <xref:System.ComponentModel.Design.MenuCommand> 類別<br /><br /> <xref:System.ComponentModel.Design.Serialization.ComponentSerializationService> 類別<br /><br /> <xref:System.ComponentModel.Design.Serialization.ContextStack> 類別<br /><br /> <xref:System.ComponentModel.Design.Serialization.DesignerLoader> 類別<br /><br /> <xref:System.ComponentModel.Design.Serialization.InstanceDescriptor> 類別<br /><br /> <xref:System.ComponentModel.Design.Serialization.MemberRelationshipService> 類別<br /><br /> <xref:System.ComponentModel.Design.Serialization.ResolveNameEventArgs> 類別<br /><br /> <xref:System.ComponentModel.Design.Serialization.ResolveNameEventHandler> 委派<br /><br /> <xref:System.ComponentModel.Design.Serialization.SerializationStore> 類別<br /><br /> <xref:System.ComponentModel.Design.ServiceContainer> 類別<br /><br /> <xref:System.ComponentModel.Design.ServiceCreatorCallback> 委派<br /><br /> <xref:System.ComponentModel.Design.StandardCommands> 類別<br /><br /> <xref:System.ComponentModel.Design.StandardToolWindows> 類別<br /><br /> <xref:System.ComponentModel.DoubleConverter> 類別<br /><br /> <xref:System.ComponentModel.DoWorkEventArgs> 類別<br /><br /> <xref:System.ComponentModel.DoWorkEventHandler> 委派<br /><br /> <xref:System.ComponentModel.EnumConverter> 類別<br /><br /> <xref:System.ComponentModel.EventDescriptor> 類別<br /><br /> <xref:System.ComponentModel.EventDescriptorCollection> 類別<br /><br /> <xref:System.ComponentModel.EventHandlerList> 類別<br /><br /> <xref:System.ComponentModel.ExpandableObjectConverter> 類別<br /><br /> <xref:System.ComponentModel.HandledEventArgs> 類別<br /><br /> <xref:System.ComponentModel.HandledEventHandler> 委派<br /><br /> <xref:System.ComponentModel.InstanceCreationEditor> 類別<br /><br /> <xref:System.ComponentModel.Int16Converter> 類別<br /><br /> <xref:System.ComponentModel.Int32Converter> 類別<br /><br /> <xref:System.ComponentModel.Int64Converter> 類別<br /><br /> <xref:System.ComponentModel.InvalidAsynchronousStateException> 類別<br /><br /> <xref:System.ComponentModel.InvalidEnumArgumentException> 類別<br /><br /> <xref:System.ComponentModel.ISynchronizeInvoke.BeginInvoke%2A> 方法<br /><br /> <xref:System.ComponentModel.License> 類別<br /><br /> <xref:System.ComponentModel.LicenseContext> 類別<br /><br /> <xref:System.ComponentModel.LicenseException> 類別<br /><br /> <xref:System.ComponentModel.LicenseManager> 類別<br /><br /> <xref:System.ComponentModel.LicenseProvider> 類別<br /><br /> <xref:System.ComponentModel.LicFileLicenseProvider> 類別<br /><br /> <xref:System.ComponentModel.ListChangedEventArgs> 類別<br /><br /> <xref:System.ComponentModel.ListChangedEventHandler> 委派<br /><br /> <xref:System.ComponentModel.ListSortDescription> 類別<br /><br /> <xref:System.ComponentModel.ListSortDescriptionCollection> 類別<br /><br /> <xref:System.ComponentModel.MaskedTextProvider> 類別<br /><br /> <xref:System.ComponentModel.MemberDescriptor> 類別<br /><br /> <xref:System.ComponentModel.MultilineStringConverter> 類別<br /><br /> <xref:System.ComponentModel.NestedContainer> 類別<br /><br /> <xref:System.ComponentModel.NullableConverter> 類別<br /><br /> <xref:System.ComponentModel.ProgressChangedEventArgs> 類別<br /><br /> <xref:System.ComponentModel.ProgressChangedEventHandler> 委派<br /><br /> <xref:System.ComponentModel.PropertyChangedEventArgs> 類別<br /><br /> <xref:System.ComponentModel.PropertyChangedEventHandler> 委派<br /><br /> <xref:System.ComponentModel.PropertyDescriptor> 類別<br /><br /> <xref:System.ComponentModel.PropertyDescriptorCollection> 類別<br /><br /> <xref:System.ComponentModel.ReferenceConverter> 類別<br /><br /> <xref:System.ComponentModel.RefreshEventArgs> 類別<br /><br /> <xref:System.ComponentModel.RefreshEventHandler> 委派<br /><br /> <xref:System.ComponentModel.RunWorkerCompletedEventArgs> 類別<br /><br /> <xref:System.ComponentModel.RunWorkerCompletedEventHandler> 委派<br /><br /> <xref:System.ComponentModel.SByteConverter> 類別<br /><br /> <xref:System.ComponentModel.SingleConverter> 類別<br /><br /> <xref:System.ComponentModel.StringConverter> 類別<br /><br /> <xref:System.ComponentModel.SyntaxCheck> 類別<br /><br /> <xref:System.ComponentModel.TimeSpanConverter> 類別<br /><br /> <xref:System.ComponentModel.TypeConverter> 類別<br /><br /> <xref:System.ComponentModel.TypeDescriptionProvider> 類別<br /><br /> <xref:System.ComponentModel.TypeDescriptor> 類別<br /><br /> <xref:System.ComponentModel.TypeListConverter> 類別<br /><br /> <xref:System.ComponentModel.UInt16Converter> 類別<br /><br /> <xref:System.ComponentModel.UInt32Converter> 類別<br /><br /> <xref:System.ComponentModel.UInt64Converter> 類別<br /><br /> <xref:System.ComponentModel.WarningException> 類別<br /><br /> <xref:System.ComponentModel.Win32Exception> 類別|  
|`System.Diagnostics`|<xref:System.Diagnostics.Debug.Listeners%2A?displayProperty=fullName> 屬性<br /><br /> <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=fullName> 屬性<br /><br /> <xref:System.Diagnostics.EventLog.SynchronizingObject%2A?displayProperty=fullName> 屬性<br /><br /> <xref:System.Diagnostics.ConsoleTraceListener> 類別<br /><br /> <xref:System.Diagnostics.DefaultTraceListener> 類別<br /><br /> <xref:System.Diagnostics.DelimitedListTraceListener> 類別<br /><br /> <xref:System.Diagnostics.EventLogTraceListener> 類別<br /><br /> <xref:System.Diagnostics.PerformanceCounter> 類別<br /><br /> <xref:System.Diagnostics.PerformanceCounterCategory> 類別<br /><br /> <xref:System.Diagnostics.Process> 類別<br /><br /> <xref:System.Diagnostics.ProcessStartInfo> 類別<br /><br /> <xref:System.Diagnostics.TextWriterTraceListener> 類別<br /><br /> <xref:System.Diagnostics.TraceListener> 類別<br /><br /> <xref:System.Diagnostics.XmlWriterTraceListener> 類別<br /><br /> <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=fullName> 屬性|  
|`System.IO`|<xref:System.IO.Stream.Synchronized%2A?displayProperty=fullName> 方法<br /><br /> <xref:System.IO.TextReader.Synchronized%2A?displayProperty=fullName> 方法<br /><br /> <xref:System.IO.TextWriter.Synchronized%2A?displayProperty=fullName> 方法|  
|`System.Reflection.Emit`|<xref:System.Reflection.Emit.ConstructorBuilder> 類別<br /><br /> <xref:System.Reflection.Emit.EventBuilder> 類別<br /><br /> <xref:System.Reflection.Emit.FieldBuilder> 類別<br /><br /> <xref:System.Reflection.Emit.MethodBuilder> 類別<br /><br /> <xref:System.Reflection.Emit.CustomAttributeBuilder> 類別<br /><br /> <xref:System.Reflection.Emit.MethodRental> 類別<br /><br /> <xref:System.Reflection.Emit.ModuleBuilder> 類別<br /><br /> <xref:System.Reflection.Emit.PropertyBuilder> 類別<br /><br /> <xref:System.Reflection.Emit.TypeBuilder> 類別<br /><br /> <xref:System.Reflection.Emit.UnmanagedMarshal> 類別|  
|`System.Text`|<xref:System.Text.RegularExpressions.Group.Synchronized%2A?displayProperty=fullName> 方法<br /><br /> <xref:System.Text.RegularExpressions.Match.Synchronized%2A?displayProperty=fullName> 方法|  
|`System.Threading`|<xref:System.Threading.AutoResetEvent> 類別<br /><br /> <xref:System.Threading.EventWaitHandle> 類別<br /><br /> <xref:System.Threading.ManualResetEvent> 類別<br /><br /> <xref:System.Threading.Monitor> 類別<br /><br /> <xref:System.Threading.Mutex> 類別<br /><br /> <xref:System.Threading.ReaderWriterLock> 類別<br /><br /> <xref:System.Threading.Semaphore> 類別<br /><br /> <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=fullName> 方法<br /><br /> <xref:System.Threading.Thread.BeginCriticalRegion%2A?displayProperty=fullName> 方法<br /><br /> <xref:System.Threading.Thread.EndCriticalRegion%2A?displayProperty=fullName> 方法<br /><br /> <xref:System.Threading.Thread.FreeNamedDataSlot%2A?displayProperty=fullName> 方法<br /><br /> <xref:System.Threading.Thread.GetData%2A?displayProperty=fullName> 方法<br /><br /> <xref:System.Threading.Thread.Join%2A?displayProperty=fullName> 方法<br /><br /> <xref:System.Threading.Thread.SetApartmentState%2A?displayProperty=fullName> 方法<br /><br /> <xref:System.Threading.Thread.SetData%2A?displayProperty=fullName> 方法<br /><br /> <xref:System.Threading.Thread.SpinWait%2A?displayProperty=fullName> 方法<br /><br /> <xref:System.Threading.Thread.Start%2A?displayProperty=fullName> 方法<br /><br /> <xref:System.Threading.Thread.TrySetApartmentState%2A?displayProperty=fullName> 方法<br /><br /> <xref:System.Threading.ThreadPool> 類別<br /><br /> <xref:System.Threading.Timer> 類別|  
|`System.Timers`|<xref:System.Timers.Timer> 類別|  
|`System.Web.Configuration`|<xref:System.Web.Configuration.MachineKeyValidationConverter> 類別|  
|`System.Windows.Forms`|<xref:System.Windows.Forms.AutoCompleteStringCollection.SyncRoot%2A?displayProperty=fullName> 屬性|  
  
## SQL Server 使用權限集合  
 SQL Server 可讓使用者針對部署到資料庫中的程式碼指定可靠性需求。  當組件上載到資料庫中時，組件的作者可以為該組件指定以下三個使用權限集合當中的一個：SAFE、EXTERNAL\-ACCESS 或 UNSAFE。  
  
|使用權限集合|SAFE|EXTERNAL\-ACCESS|UNSAFE|  
|------------|----------|----------------------|------------|  
|程式碼存取安全性|僅限執行|執行 \+ 存取外部資源|不受限|  
|程式設計模型限制|有|有|無限制|  
|可驗證性需求|有|有|沒有|  
|呼叫機器碼的能力|沒有|沒有|有|  
  
 SAFE 是最可靠及安全的模式，其包含了根據允許的程式設計模型的相關限制。  SAFE 程式碼具有高可靠性和安全性功能；  SAFE 組件有被授與足夠的權限來執行、進行運算，以及存取本機資料庫。  SAFE 組件需要是可驗證的型別安全組件，且不允許呼叫 Unmanaged 程式碼。  
  
 EXTERNAL\-ACCESS 提供了中級安全性選項，可讓程式碼存取在資料庫外部的資源，但是仍然保有 SAFE 的可靠性和安全性。  
  
 UNSAFE 適用於高度信任的程式碼，這類程式碼只能由資料庫管理員建立；  此信任的程式碼沒有程式碼存取的限制，且可以呼叫 Unmanaged 程式碼 \(機器碼\)。  
  
 SQL Server 使用主應用程式層級的程式碼存取安全性原則層來設定主應用程式原則，以根據 SQL Server 資料庫目錄中所儲存的使用權限集合來授與三個使用權限集合當中的一個。  在資料庫內執行的 Managed 程式碼一定會取得這些程式碼存取使用權限集合當中的一個。  
  
## 程式設計模型限制  
 SQL Server 中 Managed 程式碼的程式設計模型需要有函式、程序和型別，而這些項目不需要使用跨多個引動過程之間所保有的狀態或是共用跨多個使用者工作階段的狀態。  再者，如之前所述，共用狀態的存在可能會造成嚴重的例外狀況，而這些例外狀況會影響應用程式的延展性和可靠性。  
  
 基於這些考量，SQL Server 不允許使用靜態變數和靜態資料成員。  對於 SAFE 和 EXTERNAL\-ACCESS 組件而言，SQL Server 會在建立組件時檢查組件的中繼資料；如果有找到靜態資料成員和變數的使用，則會讓這類組件的建立作業失敗。  
  
## 請參閱  
 <xref:System.Security.Permissions.HostProtectionAttribute>   
 <xref:System.Security.Permissions.HostProtectionResource>