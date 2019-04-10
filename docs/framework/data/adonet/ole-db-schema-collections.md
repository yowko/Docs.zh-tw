---
title: OLE DB 結構描述集合
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 6dc187b0a876d9e167a74f2381db156dde2764fe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164680"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="52743-102">OLE DB 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="52743-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="52743-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 OLE DB 提供者的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="52743-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="52743-104">Microsoft SQL Server OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="52743-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="52743-105">Microsoft SQL Server OLE DB 驅動程式支援下列特定結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="52743-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="52743-106">資料表</span><span class="sxs-lookup"><span data-stu-id="52743-106">Tables</span></span>  
  
-   <span data-ttu-id="52743-107">資料行</span><span class="sxs-lookup"><span data-stu-id="52743-107">Columns</span></span>  
  
-   <span data-ttu-id="52743-108">程序</span><span class="sxs-lookup"><span data-stu-id="52743-108">Procedures</span></span>  
  
-   <span data-ttu-id="52743-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="52743-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="52743-110">Catalog</span><span class="sxs-lookup"><span data-stu-id="52743-110">Catalog</span></span>  
  
-   <span data-ttu-id="52743-111">索引</span><span class="sxs-lookup"><span data-stu-id="52743-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="52743-112">資料表</span><span class="sxs-lookup"><span data-stu-id="52743-112">Tables</span></span>  
  
|<span data-ttu-id="52743-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="52743-113">ColumnName</span></span>|<span data-ttu-id="52743-114">DataType</span><span class="sxs-lookup"><span data-stu-id="52743-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="52743-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-115">TABLE_CATALOG</span></span>|<span data-ttu-id="52743-116">String</span><span class="sxs-lookup"><span data-stu-id="52743-116">String</span></span>|  
|<span data-ttu-id="52743-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="52743-118">String</span><span class="sxs-lookup"><span data-stu-id="52743-118">String</span></span>|  
|<span data-ttu-id="52743-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-119">TABLE_NAME</span></span>|<span data-ttu-id="52743-120">String</span><span class="sxs-lookup"><span data-stu-id="52743-120">String</span></span>|  
|<span data-ttu-id="52743-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="52743-121">TABLE_TYPE</span></span>|<span data-ttu-id="52743-122">String</span><span class="sxs-lookup"><span data-stu-id="52743-122">String</span></span>|  
|<span data-ttu-id="52743-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="52743-123">TABLE_GUID</span></span>|<span data-ttu-id="52743-124">Guid</span><span class="sxs-lookup"><span data-stu-id="52743-124">Guid</span></span>|  
|<span data-ttu-id="52743-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="52743-125">DESCRIPTION</span></span>|<span data-ttu-id="52743-126">String</span><span class="sxs-lookup"><span data-stu-id="52743-126">String</span></span>|  
|<span data-ttu-id="52743-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="52743-127">TABLE_PROPID</span></span>|<span data-ttu-id="52743-128">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-128">Int64</span></span>|  
|<span data-ttu-id="52743-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="52743-129">DATE_CREATED</span></span>|<span data-ttu-id="52743-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="52743-130">DateTime</span></span>|  
|<span data-ttu-id="52743-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="52743-131">DATE_MODIFIED</span></span>|<span data-ttu-id="52743-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="52743-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="52743-133">資料行</span><span class="sxs-lookup"><span data-stu-id="52743-133">Columns</span></span>  
  
|<span data-ttu-id="52743-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="52743-134">ColumnName</span></span>|<span data-ttu-id="52743-135">DataType</span><span class="sxs-lookup"><span data-stu-id="52743-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="52743-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-136">TABLE_CATALOG</span></span>|<span data-ttu-id="52743-137">String</span><span class="sxs-lookup"><span data-stu-id="52743-137">String</span></span>|  
|<span data-ttu-id="52743-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="52743-139">String</span><span class="sxs-lookup"><span data-stu-id="52743-139">String</span></span>|  
|<span data-ttu-id="52743-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-140">TABLE_NAME</span></span>|<span data-ttu-id="52743-141">String</span><span class="sxs-lookup"><span data-stu-id="52743-141">String</span></span>|  
|<span data-ttu-id="52743-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-142">COLUMN_NAME</span></span>|<span data-ttu-id="52743-143">String</span><span class="sxs-lookup"><span data-stu-id="52743-143">String</span></span>|  
|<span data-ttu-id="52743-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="52743-144">COLUMN_GUID</span></span>|<span data-ttu-id="52743-145">Guid</span><span class="sxs-lookup"><span data-stu-id="52743-145">Guid</span></span>|  
|<span data-ttu-id="52743-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="52743-146">COLUMN_PROPID</span></span>|<span data-ttu-id="52743-147">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-147">Int64</span></span>|  
|<span data-ttu-id="52743-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="52743-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="52743-149">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-149">Int64</span></span>|  
|<span data-ttu-id="52743-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="52743-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="52743-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-151">Boolean</span></span>|  
|<span data-ttu-id="52743-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="52743-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="52743-153">String</span><span class="sxs-lookup"><span data-stu-id="52743-153">String</span></span>|  
|<span data-ttu-id="52743-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="52743-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="52743-155">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-155">Int64</span></span>|  
|<span data-ttu-id="52743-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="52743-156">IS_NULLABLE</span></span>|<span data-ttu-id="52743-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-157">Boolean</span></span>|  
|<span data-ttu-id="52743-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="52743-158">DATA_TYPE</span></span>|<span data-ttu-id="52743-159">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-159">Int32</span></span>|  
|<span data-ttu-id="52743-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="52743-160">TYPE_GUID</span></span>|<span data-ttu-id="52743-161">Guid</span><span class="sxs-lookup"><span data-stu-id="52743-161">Guid</span></span>|  
|<span data-ttu-id="52743-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="52743-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="52743-163">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-163">Int64</span></span>|  
|<span data-ttu-id="52743-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="52743-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="52743-165">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-165">Int64</span></span>|  
|<span data-ttu-id="52743-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="52743-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="52743-167">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-167">Int32</span></span>|  
|<span data-ttu-id="52743-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="52743-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="52743-169">Int16</span><span class="sxs-lookup"><span data-stu-id="52743-169">Int16</span></span>|  
|<span data-ttu-id="52743-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="52743-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="52743-171">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-171">Int64</span></span>|  
|<span data-ttu-id="52743-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="52743-173">String</span><span class="sxs-lookup"><span data-stu-id="52743-173">String</span></span>|  
|<span data-ttu-id="52743-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="52743-175">String</span><span class="sxs-lookup"><span data-stu-id="52743-175">String</span></span>|  
|<span data-ttu-id="52743-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="52743-177">String</span><span class="sxs-lookup"><span data-stu-id="52743-177">String</span></span>|  
|<span data-ttu-id="52743-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="52743-179">String</span><span class="sxs-lookup"><span data-stu-id="52743-179">String</span></span>|  
|<span data-ttu-id="52743-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="52743-181">String</span><span class="sxs-lookup"><span data-stu-id="52743-181">String</span></span>|  
|<span data-ttu-id="52743-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-182">COLLATION_NAME</span></span>|<span data-ttu-id="52743-183">String</span><span class="sxs-lookup"><span data-stu-id="52743-183">String</span></span>|  
|<span data-ttu-id="52743-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="52743-185">String</span><span class="sxs-lookup"><span data-stu-id="52743-185">String</span></span>|  
|<span data-ttu-id="52743-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="52743-187">String</span><span class="sxs-lookup"><span data-stu-id="52743-187">String</span></span>|  
|<span data-ttu-id="52743-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-188">DOMAIN_NAME</span></span>|<span data-ttu-id="52743-189">String</span><span class="sxs-lookup"><span data-stu-id="52743-189">String</span></span>|  
|<span data-ttu-id="52743-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="52743-190">DESCRIPTION</span></span>|<span data-ttu-id="52743-191">String</span><span class="sxs-lookup"><span data-stu-id="52743-191">String</span></span>|  
|<span data-ttu-id="52743-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="52743-192">COLUMN_LCID</span></span>|<span data-ttu-id="52743-193">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-193">Int32</span></span>|  
|<span data-ttu-id="52743-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="52743-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="52743-195">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-195">Int32</span></span>|  
|<span data-ttu-id="52743-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="52743-196">COLUMN_SORTID</span></span>|<span data-ttu-id="52743-197">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-197">Int32</span></span>|  
|<span data-ttu-id="52743-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="52743-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="52743-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="52743-199">Byte[]</span></span>|  
|<span data-ttu-id="52743-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="52743-200">IS_COMPUTED</span></span>|<span data-ttu-id="52743-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="52743-202">程序</span><span class="sxs-lookup"><span data-stu-id="52743-202">Procedures</span></span>  
  
|<span data-ttu-id="52743-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="52743-203">ColumnName</span></span>|<span data-ttu-id="52743-204">DataType</span><span class="sxs-lookup"><span data-stu-id="52743-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="52743-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="52743-206">String</span><span class="sxs-lookup"><span data-stu-id="52743-206">String</span></span>|  
|<span data-ttu-id="52743-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="52743-208">String</span><span class="sxs-lookup"><span data-stu-id="52743-208">String</span></span>|  
|<span data-ttu-id="52743-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="52743-210">String</span><span class="sxs-lookup"><span data-stu-id="52743-210">String</span></span>|  
|<span data-ttu-id="52743-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="52743-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="52743-212">Int16</span><span class="sxs-lookup"><span data-stu-id="52743-212">Int16</span></span>|  
|<span data-ttu-id="52743-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="52743-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="52743-214">String</span><span class="sxs-lookup"><span data-stu-id="52743-214">String</span></span>|  
|<span data-ttu-id="52743-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="52743-215">DESCRIPTION</span></span>|<span data-ttu-id="52743-216">String</span><span class="sxs-lookup"><span data-stu-id="52743-216">String</span></span>|  
|<span data-ttu-id="52743-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="52743-217">DATE_CREATED</span></span>|<span data-ttu-id="52743-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="52743-218">DateTime</span></span>|  
|<span data-ttu-id="52743-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="52743-219">DATE_MODIFIED</span></span>|<span data-ttu-id="52743-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="52743-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="52743-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="52743-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="52743-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="52743-222">ColumnName</span></span>|<span data-ttu-id="52743-223">DataType</span><span class="sxs-lookup"><span data-stu-id="52743-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="52743-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="52743-225">String</span><span class="sxs-lookup"><span data-stu-id="52743-225">String</span></span>|  
|<span data-ttu-id="52743-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="52743-227">String</span><span class="sxs-lookup"><span data-stu-id="52743-227">String</span></span>|  
|<span data-ttu-id="52743-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="52743-229">String</span><span class="sxs-lookup"><span data-stu-id="52743-229">String</span></span>|  
|<span data-ttu-id="52743-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-230">PARAMETER_NAME</span></span>|<span data-ttu-id="52743-231">String</span><span class="sxs-lookup"><span data-stu-id="52743-231">String</span></span>|  
|<span data-ttu-id="52743-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="52743-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="52743-233">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-233">Int32</span></span>|  
|<span data-ttu-id="52743-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="52743-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="52743-235">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-235">Int32</span></span>|  
|<span data-ttu-id="52743-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="52743-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="52743-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-237">Boolean</span></span>|  
|<span data-ttu-id="52743-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="52743-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="52743-239">String</span><span class="sxs-lookup"><span data-stu-id="52743-239">String</span></span>|  
|<span data-ttu-id="52743-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="52743-240">IS_NULLABLE</span></span>|<span data-ttu-id="52743-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-241">Boolean</span></span>|  
|<span data-ttu-id="52743-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="52743-242">DATA_TYPE</span></span>|<span data-ttu-id="52743-243">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-243">Int32</span></span>|  
|<span data-ttu-id="52743-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="52743-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="52743-245">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-245">Int64</span></span>|  
|<span data-ttu-id="52743-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="52743-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="52743-247">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-247">Int64</span></span>|  
|<span data-ttu-id="52743-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="52743-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="52743-249">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-249">Int32</span></span>|  
|<span data-ttu-id="52743-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="52743-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="52743-251">Int16</span><span class="sxs-lookup"><span data-stu-id="52743-251">Int16</span></span>|  
|<span data-ttu-id="52743-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="52743-252">DESCRIPTION</span></span>|<span data-ttu-id="52743-253">String</span><span class="sxs-lookup"><span data-stu-id="52743-253">String</span></span>|  
|<span data-ttu-id="52743-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-254">TYPE_NAME</span></span>|<span data-ttu-id="52743-255">String</span><span class="sxs-lookup"><span data-stu-id="52743-255">String</span></span>|  
|<span data-ttu-id="52743-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="52743-257">String</span><span class="sxs-lookup"><span data-stu-id="52743-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="52743-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="52743-258">Catalog</span></span>  
  
|<span data-ttu-id="52743-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="52743-259">ColumnName</span></span>|<span data-ttu-id="52743-260">DataType</span><span class="sxs-lookup"><span data-stu-id="52743-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="52743-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-261">CATALOG_NAME</span></span>|<span data-ttu-id="52743-262">String</span><span class="sxs-lookup"><span data-stu-id="52743-262">String</span></span>|  
|<span data-ttu-id="52743-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="52743-263">DESCRIPTION</span></span>|<span data-ttu-id="52743-264">String</span><span class="sxs-lookup"><span data-stu-id="52743-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="52743-265">索引</span><span class="sxs-lookup"><span data-stu-id="52743-265">Indexes</span></span>  
  
|<span data-ttu-id="52743-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="52743-266">ColumnName</span></span>|<span data-ttu-id="52743-267">DataType</span><span class="sxs-lookup"><span data-stu-id="52743-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="52743-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-268">TABLE_CATALOG</span></span>|<span data-ttu-id="52743-269">String</span><span class="sxs-lookup"><span data-stu-id="52743-269">String</span></span>|  
|<span data-ttu-id="52743-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="52743-271">String</span><span class="sxs-lookup"><span data-stu-id="52743-271">String</span></span>|  
|<span data-ttu-id="52743-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-272">TABLE_NAME</span></span>|<span data-ttu-id="52743-273">String</span><span class="sxs-lookup"><span data-stu-id="52743-273">String</span></span>|  
|<span data-ttu-id="52743-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-274">INDEX_CATALOG</span></span>|<span data-ttu-id="52743-275">String</span><span class="sxs-lookup"><span data-stu-id="52743-275">String</span></span>|  
|<span data-ttu-id="52743-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="52743-277">String</span><span class="sxs-lookup"><span data-stu-id="52743-277">String</span></span>|  
|<span data-ttu-id="52743-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-278">INDEX_NAME</span></span>|<span data-ttu-id="52743-279">String</span><span class="sxs-lookup"><span data-stu-id="52743-279">String</span></span>|  
|<span data-ttu-id="52743-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="52743-280">PRIMARY_KEY</span></span>|<span data-ttu-id="52743-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-281">Boolean</span></span>|  
|<span data-ttu-id="52743-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="52743-282">UNIQUE</span></span>|<span data-ttu-id="52743-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-283">Boolean</span></span>|  
|<span data-ttu-id="52743-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="52743-284">CLUSTERED</span></span>|<span data-ttu-id="52743-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-285">Boolean</span></span>|  
|<span data-ttu-id="52743-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="52743-286">TYPE</span></span>|<span data-ttu-id="52743-287">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-287">Int32</span></span>|  
|<span data-ttu-id="52743-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="52743-288">FILL_FACTOR</span></span>|<span data-ttu-id="52743-289">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-289">Int32</span></span>|  
|<span data-ttu-id="52743-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="52743-290">INITIAL_SIZE</span></span>|<span data-ttu-id="52743-291">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-291">Int32</span></span>|  
|<span data-ttu-id="52743-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="52743-292">NULLS</span></span>|<span data-ttu-id="52743-293">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-293">Int32</span></span>|  
|<span data-ttu-id="52743-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="52743-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="52743-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-295">Boolean</span></span>|  
|<span data-ttu-id="52743-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="52743-296">AUTO_UPDATE</span></span>|<span data-ttu-id="52743-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-297">Boolean</span></span>|  
|<span data-ttu-id="52743-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="52743-298">NULL_COLLATION</span></span>|<span data-ttu-id="52743-299">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-299">Int32</span></span>|  
|<span data-ttu-id="52743-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="52743-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="52743-301">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-301">Int64</span></span>|  
|<span data-ttu-id="52743-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-302">COLUMN_NAME</span></span>|<span data-ttu-id="52743-303">String</span><span class="sxs-lookup"><span data-stu-id="52743-303">String</span></span>|  
|<span data-ttu-id="52743-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="52743-304">COLUMN_GUID</span></span>|<span data-ttu-id="52743-305">Guid</span><span class="sxs-lookup"><span data-stu-id="52743-305">Guid</span></span>|  
|<span data-ttu-id="52743-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="52743-306">COLUMN_PROPID</span></span>|<span data-ttu-id="52743-307">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-307">Int64</span></span>|  
|<span data-ttu-id="52743-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="52743-308">COLLATION</span></span>|<span data-ttu-id="52743-309">Int16</span><span class="sxs-lookup"><span data-stu-id="52743-309">Int16</span></span>|  
|<span data-ttu-id="52743-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="52743-310">CARDINALITY</span></span>|<span data-ttu-id="52743-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="52743-311">Decimal</span></span>|  
|<span data-ttu-id="52743-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="52743-312">PAGES</span></span>|<span data-ttu-id="52743-313">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-313">Int32</span></span>|  
|<span data-ttu-id="52743-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="52743-314">FILTER_CONDITION</span></span>|<span data-ttu-id="52743-315">String</span><span class="sxs-lookup"><span data-stu-id="52743-315">String</span></span>|  
|<span data-ttu-id="52743-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="52743-316">INTEGRATED</span></span>|<span data-ttu-id="52743-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="52743-318">Microsoft Oracle OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="52743-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="52743-319">除了通用結構描述集合之外，Microsoft Oracle OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="52743-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="52743-320">資料表</span><span class="sxs-lookup"><span data-stu-id="52743-320">Tables</span></span>  
  
-   <span data-ttu-id="52743-321">資料行</span><span class="sxs-lookup"><span data-stu-id="52743-321">Columns</span></span>  
  
-   <span data-ttu-id="52743-322">程序</span><span class="sxs-lookup"><span data-stu-id="52743-322">Procedures</span></span>  
  
-   <span data-ttu-id="52743-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="52743-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="52743-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="52743-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="52743-325">檢視</span><span class="sxs-lookup"><span data-stu-id="52743-325">Views</span></span>  
  
-   <span data-ttu-id="52743-326">索引</span><span class="sxs-lookup"><span data-stu-id="52743-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="52743-327">資料表</span><span class="sxs-lookup"><span data-stu-id="52743-327">Tables</span></span>  
  
|<span data-ttu-id="52743-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="52743-328">ColumnName</span></span>|<span data-ttu-id="52743-329">DataType</span><span class="sxs-lookup"><span data-stu-id="52743-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="52743-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-330">TABLE_CATALOG</span></span>|<span data-ttu-id="52743-331">String</span><span class="sxs-lookup"><span data-stu-id="52743-331">String</span></span>|  
|<span data-ttu-id="52743-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="52743-333">String</span><span class="sxs-lookup"><span data-stu-id="52743-333">String</span></span>|  
|<span data-ttu-id="52743-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-334">TABLE_NAME</span></span>|<span data-ttu-id="52743-335">String</span><span class="sxs-lookup"><span data-stu-id="52743-335">String</span></span>|  
|<span data-ttu-id="52743-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="52743-336">TABLE_TYPE</span></span>|<span data-ttu-id="52743-337">String</span><span class="sxs-lookup"><span data-stu-id="52743-337">String</span></span>|  
|<span data-ttu-id="52743-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="52743-338">TABLE_GUID</span></span>|<span data-ttu-id="52743-339">Guid</span><span class="sxs-lookup"><span data-stu-id="52743-339">Guid</span></span>|  
|<span data-ttu-id="52743-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="52743-340">DESCRIPTION</span></span>|<span data-ttu-id="52743-341">String</span><span class="sxs-lookup"><span data-stu-id="52743-341">String</span></span>|  
|<span data-ttu-id="52743-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="52743-342">TABLE_PROPID</span></span>|<span data-ttu-id="52743-343">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-343">Int64</span></span>|  
|<span data-ttu-id="52743-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="52743-344">DATE_CREATED</span></span>|<span data-ttu-id="52743-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="52743-345">DateTime</span></span>|  
|<span data-ttu-id="52743-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="52743-346">DATE_MODIFIED</span></span>|<span data-ttu-id="52743-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="52743-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="52743-348">資料行</span><span class="sxs-lookup"><span data-stu-id="52743-348">Columns</span></span>  
  
|<span data-ttu-id="52743-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="52743-349">ColumnName</span></span>|<span data-ttu-id="52743-350">DataType</span><span class="sxs-lookup"><span data-stu-id="52743-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="52743-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-351">TABLE_CATALOG</span></span>|<span data-ttu-id="52743-352">String</span><span class="sxs-lookup"><span data-stu-id="52743-352">String</span></span>|  
|<span data-ttu-id="52743-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="52743-354">String</span><span class="sxs-lookup"><span data-stu-id="52743-354">String</span></span>|  
|<span data-ttu-id="52743-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-355">TABLE_NAME</span></span>|<span data-ttu-id="52743-356">String</span><span class="sxs-lookup"><span data-stu-id="52743-356">String</span></span>|  
|<span data-ttu-id="52743-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-357">COLUMN_NAME</span></span>|<span data-ttu-id="52743-358">String</span><span class="sxs-lookup"><span data-stu-id="52743-358">String</span></span>|  
|<span data-ttu-id="52743-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="52743-359">COLUMN_GUID</span></span>|<span data-ttu-id="52743-360">Guid</span><span class="sxs-lookup"><span data-stu-id="52743-360">Guid</span></span>|  
|<span data-ttu-id="52743-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="52743-361">COLUMN_PROPID</span></span>|<span data-ttu-id="52743-362">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-362">Int64</span></span>|  
|<span data-ttu-id="52743-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="52743-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="52743-364">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-364">Int64</span></span>|  
|<span data-ttu-id="52743-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="52743-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="52743-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-366">Boolean</span></span>|  
|<span data-ttu-id="52743-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="52743-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="52743-368">String</span><span class="sxs-lookup"><span data-stu-id="52743-368">String</span></span>|  
|<span data-ttu-id="52743-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="52743-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="52743-370">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-370">Int64</span></span>|  
|<span data-ttu-id="52743-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="52743-371">IS_NULLABLE</span></span>|<span data-ttu-id="52743-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-372">Boolean</span></span>|  
|<span data-ttu-id="52743-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="52743-373">DATA_TYPE</span></span>|<span data-ttu-id="52743-374">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-374">Int32</span></span>|  
|<span data-ttu-id="52743-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="52743-375">TYPE_GUID</span></span>|<span data-ttu-id="52743-376">Guid</span><span class="sxs-lookup"><span data-stu-id="52743-376">Guid</span></span>|  
|<span data-ttu-id="52743-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="52743-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="52743-378">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-378">Int64</span></span>|  
|<span data-ttu-id="52743-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="52743-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="52743-380">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-380">Int64</span></span>|  
|<span data-ttu-id="52743-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="52743-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="52743-382">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-382">Int32</span></span>|  
|<span data-ttu-id="52743-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="52743-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="52743-384">Int16</span><span class="sxs-lookup"><span data-stu-id="52743-384">Int16</span></span>|  
|<span data-ttu-id="52743-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="52743-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="52743-386">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-386">Int64</span></span>|  
|<span data-ttu-id="52743-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="52743-388">String</span><span class="sxs-lookup"><span data-stu-id="52743-388">String</span></span>|  
|<span data-ttu-id="52743-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="52743-390">String</span><span class="sxs-lookup"><span data-stu-id="52743-390">String</span></span>|  
|<span data-ttu-id="52743-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="52743-392">String</span><span class="sxs-lookup"><span data-stu-id="52743-392">String</span></span>|  
|<span data-ttu-id="52743-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="52743-394">String</span><span class="sxs-lookup"><span data-stu-id="52743-394">String</span></span>|  
|<span data-ttu-id="52743-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="52743-396">String</span><span class="sxs-lookup"><span data-stu-id="52743-396">String</span></span>|  
|<span data-ttu-id="52743-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-397">COLLATION_NAME</span></span>|<span data-ttu-id="52743-398">String</span><span class="sxs-lookup"><span data-stu-id="52743-398">String</span></span>|  
|<span data-ttu-id="52743-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="52743-400">String</span><span class="sxs-lookup"><span data-stu-id="52743-400">String</span></span>|  
|<span data-ttu-id="52743-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="52743-402">String</span><span class="sxs-lookup"><span data-stu-id="52743-402">String</span></span>|  
|<span data-ttu-id="52743-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-403">DOMAIN_NAME</span></span>|<span data-ttu-id="52743-404">String</span><span class="sxs-lookup"><span data-stu-id="52743-404">String</span></span>|  
|<span data-ttu-id="52743-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="52743-405">DESCRIPTION</span></span>|<span data-ttu-id="52743-406">String</span><span class="sxs-lookup"><span data-stu-id="52743-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="52743-407">程序</span><span class="sxs-lookup"><span data-stu-id="52743-407">Procedures</span></span>  
  
|<span data-ttu-id="52743-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="52743-408">ColumnName</span></span>|<span data-ttu-id="52743-409">DataType</span><span class="sxs-lookup"><span data-stu-id="52743-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="52743-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="52743-411">String</span><span class="sxs-lookup"><span data-stu-id="52743-411">String</span></span>|  
|<span data-ttu-id="52743-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="52743-413">String</span><span class="sxs-lookup"><span data-stu-id="52743-413">String</span></span>|  
|<span data-ttu-id="52743-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="52743-415">String</span><span class="sxs-lookup"><span data-stu-id="52743-415">String</span></span>|  
|<span data-ttu-id="52743-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="52743-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="52743-417">Int16</span><span class="sxs-lookup"><span data-stu-id="52743-417">Int16</span></span>|  
|<span data-ttu-id="52743-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="52743-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="52743-419">String</span><span class="sxs-lookup"><span data-stu-id="52743-419">String</span></span>|  
|<span data-ttu-id="52743-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="52743-420">DESCRIPTION</span></span>|<span data-ttu-id="52743-421">String</span><span class="sxs-lookup"><span data-stu-id="52743-421">String</span></span>|  
|<span data-ttu-id="52743-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="52743-422">DATE_CREATED</span></span>|<span data-ttu-id="52743-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="52743-423">DateTime</span></span>|  
|<span data-ttu-id="52743-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="52743-424">DATE_MODIFIED</span></span>|<span data-ttu-id="52743-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="52743-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="52743-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="52743-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="52743-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="52743-427">ColumnName</span></span>|<span data-ttu-id="52743-428">DataType</span><span class="sxs-lookup"><span data-stu-id="52743-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="52743-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="52743-430">String</span><span class="sxs-lookup"><span data-stu-id="52743-430">String</span></span>|  
|<span data-ttu-id="52743-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="52743-432">String</span><span class="sxs-lookup"><span data-stu-id="52743-432">String</span></span>|  
|<span data-ttu-id="52743-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="52743-434">String</span><span class="sxs-lookup"><span data-stu-id="52743-434">String</span></span>|  
|<span data-ttu-id="52743-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-435">COLUMN_NAME</span></span>|<span data-ttu-id="52743-436">String</span><span class="sxs-lookup"><span data-stu-id="52743-436">String</span></span>|  
|<span data-ttu-id="52743-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="52743-437">COLUMN_GUID</span></span>|<span data-ttu-id="52743-438">Guid</span><span class="sxs-lookup"><span data-stu-id="52743-438">Guid</span></span>|  
|<span data-ttu-id="52743-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="52743-439">COLUMN_PROPID</span></span>|<span data-ttu-id="52743-440">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-440">Int64</span></span>|  
|<span data-ttu-id="52743-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="52743-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="52743-442">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-442">Int64</span></span>|  
|<span data-ttu-id="52743-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="52743-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="52743-444">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-444">Int64</span></span>|  
|<span data-ttu-id="52743-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="52743-445">IS_NULLABLE</span></span>|<span data-ttu-id="52743-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-446">Boolean</span></span>|  
|<span data-ttu-id="52743-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="52743-447">DATA_TYPE</span></span>|<span data-ttu-id="52743-448">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-448">Int32</span></span>|  
|<span data-ttu-id="52743-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="52743-449">TYPE_GUID</span></span>|<span data-ttu-id="52743-450">Guid</span><span class="sxs-lookup"><span data-stu-id="52743-450">Guid</span></span>|  
|<span data-ttu-id="52743-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="52743-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="52743-452">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-452">Int64</span></span>|  
|<span data-ttu-id="52743-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="52743-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="52743-454">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-454">Int64</span></span>|  
|<span data-ttu-id="52743-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="52743-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="52743-456">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-456">Int32</span></span>|  
|<span data-ttu-id="52743-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="52743-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="52743-458">Int16</span><span class="sxs-lookup"><span data-stu-id="52743-458">Int16</span></span>|  
|<span data-ttu-id="52743-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="52743-459">DESCRIPTION</span></span>|<span data-ttu-id="52743-460">String</span><span class="sxs-lookup"><span data-stu-id="52743-460">String</span></span>|  
|<span data-ttu-id="52743-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="52743-461">OVERLOAD</span></span>|<span data-ttu-id="52743-462">Int16</span><span class="sxs-lookup"><span data-stu-id="52743-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="52743-463">檢視</span><span class="sxs-lookup"><span data-stu-id="52743-463">Views</span></span>  
  
|<span data-ttu-id="52743-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="52743-464">ColumnName</span></span>|<span data-ttu-id="52743-465">DataType</span><span class="sxs-lookup"><span data-stu-id="52743-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="52743-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-466">TABLE_CATALOG</span></span>|<span data-ttu-id="52743-467">String</span><span class="sxs-lookup"><span data-stu-id="52743-467">String</span></span>|  
|<span data-ttu-id="52743-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="52743-469">String</span><span class="sxs-lookup"><span data-stu-id="52743-469">String</span></span>|  
|<span data-ttu-id="52743-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-470">TABLE_NAME</span></span>|<span data-ttu-id="52743-471">String</span><span class="sxs-lookup"><span data-stu-id="52743-471">String</span></span>|  
|<span data-ttu-id="52743-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="52743-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="52743-473">String</span><span class="sxs-lookup"><span data-stu-id="52743-473">String</span></span>|  
|<span data-ttu-id="52743-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="52743-474">CHECK_OPTION</span></span>|<span data-ttu-id="52743-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-475">Boolean</span></span>|  
|<span data-ttu-id="52743-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="52743-476">IS_UPDATABLE</span></span>|<span data-ttu-id="52743-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-477">Boolean</span></span>|  
|<span data-ttu-id="52743-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="52743-478">DESCRIPTION</span></span>|<span data-ttu-id="52743-479">String</span><span class="sxs-lookup"><span data-stu-id="52743-479">String</span></span>|  
|<span data-ttu-id="52743-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="52743-480">DATE_CREATED</span></span>|<span data-ttu-id="52743-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="52743-481">DateTime</span></span>|  
|<span data-ttu-id="52743-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="52743-482">DATE_MODIFIED</span></span>|<span data-ttu-id="52743-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="52743-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="52743-484">索引</span><span class="sxs-lookup"><span data-stu-id="52743-484">Indexes</span></span>  
  
|<span data-ttu-id="52743-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="52743-485">ColumnName</span></span>|<span data-ttu-id="52743-486">DataType</span><span class="sxs-lookup"><span data-stu-id="52743-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="52743-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-487">TABLE_CATALOG</span></span>|<span data-ttu-id="52743-488">String</span><span class="sxs-lookup"><span data-stu-id="52743-488">String</span></span>|  
|<span data-ttu-id="52743-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="52743-490">String</span><span class="sxs-lookup"><span data-stu-id="52743-490">String</span></span>|  
|<span data-ttu-id="52743-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-491">TABLE_NAME</span></span>|<span data-ttu-id="52743-492">String</span><span class="sxs-lookup"><span data-stu-id="52743-492">String</span></span>|  
|<span data-ttu-id="52743-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-493">INDEX_CATALOG</span></span>|<span data-ttu-id="52743-494">String</span><span class="sxs-lookup"><span data-stu-id="52743-494">String</span></span>|  
|<span data-ttu-id="52743-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="52743-496">String</span><span class="sxs-lookup"><span data-stu-id="52743-496">String</span></span>|  
|<span data-ttu-id="52743-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-497">INDEX_NAME</span></span>|<span data-ttu-id="52743-498">String</span><span class="sxs-lookup"><span data-stu-id="52743-498">String</span></span>|  
|<span data-ttu-id="52743-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="52743-499">PRIMARY_KEY</span></span>|<span data-ttu-id="52743-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-500">Boolean</span></span>|  
|<span data-ttu-id="52743-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="52743-501">UNIQUE</span></span>|<span data-ttu-id="52743-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-502">Boolean</span></span>|  
|<span data-ttu-id="52743-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="52743-503">CLUSTERED</span></span>|<span data-ttu-id="52743-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-504">Boolean</span></span>|  
|<span data-ttu-id="52743-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="52743-505">TYPE</span></span>|<span data-ttu-id="52743-506">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-506">Int32</span></span>|  
|<span data-ttu-id="52743-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="52743-507">FILL_FACTOR</span></span>|<span data-ttu-id="52743-508">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-508">Int32</span></span>|  
|<span data-ttu-id="52743-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="52743-509">INITIAL_SIZE</span></span>|<span data-ttu-id="52743-510">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-510">Int32</span></span>|  
|<span data-ttu-id="52743-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="52743-511">NULLS</span></span>|<span data-ttu-id="52743-512">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-512">Int32</span></span>|  
|<span data-ttu-id="52743-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="52743-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="52743-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-514">Boolean</span></span>|  
|<span data-ttu-id="52743-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="52743-515">AUTO_UPDATE</span></span>|<span data-ttu-id="52743-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-516">Boolean</span></span>|  
|<span data-ttu-id="52743-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="52743-517">NULL_COLLATION</span></span>|<span data-ttu-id="52743-518">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-518">Int32</span></span>|  
|<span data-ttu-id="52743-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="52743-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="52743-520">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-520">Int64</span></span>|  
|<span data-ttu-id="52743-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-521">COLUMN_NAME</span></span>|<span data-ttu-id="52743-522">String</span><span class="sxs-lookup"><span data-stu-id="52743-522">String</span></span>|  
|<span data-ttu-id="52743-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="52743-523">COLUMN_GUID</span></span>|<span data-ttu-id="52743-524">Guid</span><span class="sxs-lookup"><span data-stu-id="52743-524">Guid</span></span>|  
|<span data-ttu-id="52743-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="52743-525">COLUMN_PROPID</span></span>|<span data-ttu-id="52743-526">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-526">Int64</span></span>|  
|<span data-ttu-id="52743-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="52743-527">COLLATION</span></span>|<span data-ttu-id="52743-528">Int16</span><span class="sxs-lookup"><span data-stu-id="52743-528">Int16</span></span>|  
|<span data-ttu-id="52743-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="52743-529">CARDINALITY</span></span>|<span data-ttu-id="52743-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="52743-530">Decimal</span></span>|  
|<span data-ttu-id="52743-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="52743-531">PAGES</span></span>|<span data-ttu-id="52743-532">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-532">Int32</span></span>|  
|<span data-ttu-id="52743-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="52743-533">FILTER_CONDITION</span></span>|<span data-ttu-id="52743-534">String</span><span class="sxs-lookup"><span data-stu-id="52743-534">String</span></span>|  
|<span data-ttu-id="52743-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="52743-535">INTEGRATED</span></span>|<span data-ttu-id="52743-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="52743-537">Microsoft Jet OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="52743-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="52743-538">除了通用結構描述集合之外，Microsoft Jet OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="52743-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="52743-539">資料表</span><span class="sxs-lookup"><span data-stu-id="52743-539">Tables</span></span>  
  
-   <span data-ttu-id="52743-540">資料行</span><span class="sxs-lookup"><span data-stu-id="52743-540">Columns</span></span>  
  
-   <span data-ttu-id="52743-541">程序</span><span class="sxs-lookup"><span data-stu-id="52743-541">Procedures</span></span>  
  
-   <span data-ttu-id="52743-542">檢視</span><span class="sxs-lookup"><span data-stu-id="52743-542">Views</span></span>  
  
-   <span data-ttu-id="52743-543">索引</span><span class="sxs-lookup"><span data-stu-id="52743-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="52743-544">資料表</span><span class="sxs-lookup"><span data-stu-id="52743-544">Tables</span></span>  
  
|<span data-ttu-id="52743-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="52743-545">ColumnName</span></span>|<span data-ttu-id="52743-546">DataType</span><span class="sxs-lookup"><span data-stu-id="52743-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="52743-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-547">TABLE_CATALOG</span></span>|<span data-ttu-id="52743-548">String</span><span class="sxs-lookup"><span data-stu-id="52743-548">String</span></span>|  
|<span data-ttu-id="52743-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="52743-550">String</span><span class="sxs-lookup"><span data-stu-id="52743-550">String</span></span>|  
|<span data-ttu-id="52743-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-551">TABLE_NAME</span></span>|<span data-ttu-id="52743-552">String</span><span class="sxs-lookup"><span data-stu-id="52743-552">String</span></span>|  
|<span data-ttu-id="52743-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="52743-553">TABLE_TYPE</span></span>|<span data-ttu-id="52743-554">String</span><span class="sxs-lookup"><span data-stu-id="52743-554">String</span></span>|  
|<span data-ttu-id="52743-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="52743-555">TABLE_GUID</span></span>|<span data-ttu-id="52743-556">Guid</span><span class="sxs-lookup"><span data-stu-id="52743-556">Guid</span></span>|  
|<span data-ttu-id="52743-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="52743-557">DESCRIPTION</span></span>|<span data-ttu-id="52743-558">String</span><span class="sxs-lookup"><span data-stu-id="52743-558">String</span></span>|  
|<span data-ttu-id="52743-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="52743-559">TABLE_PROPID</span></span>|<span data-ttu-id="52743-560">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-560">Int64</span></span>|  
|<span data-ttu-id="52743-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="52743-561">DATE_CREATED</span></span>|<span data-ttu-id="52743-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="52743-562">DateTime</span></span>|  
|<span data-ttu-id="52743-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="52743-563">DATE_MODIFIED</span></span>|<span data-ttu-id="52743-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="52743-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="52743-565">資料行</span><span class="sxs-lookup"><span data-stu-id="52743-565">Columns</span></span>  
  
|<span data-ttu-id="52743-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="52743-566">ColumnName</span></span>|<span data-ttu-id="52743-567">DataType</span><span class="sxs-lookup"><span data-stu-id="52743-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="52743-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-568">TABLE_CATALOG</span></span>|<span data-ttu-id="52743-569">String</span><span class="sxs-lookup"><span data-stu-id="52743-569">String</span></span>|  
|<span data-ttu-id="52743-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="52743-571">String</span><span class="sxs-lookup"><span data-stu-id="52743-571">String</span></span>|  
|<span data-ttu-id="52743-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-572">TABLE_NAME</span></span>|<span data-ttu-id="52743-573">String</span><span class="sxs-lookup"><span data-stu-id="52743-573">String</span></span>|  
|<span data-ttu-id="52743-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-574">COLUMN_NAME</span></span>|<span data-ttu-id="52743-575">String</span><span class="sxs-lookup"><span data-stu-id="52743-575">String</span></span>|  
|<span data-ttu-id="52743-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="52743-576">COLUMN_GUID</span></span>|<span data-ttu-id="52743-577">Guid</span><span class="sxs-lookup"><span data-stu-id="52743-577">Guid</span></span>|  
|<span data-ttu-id="52743-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="52743-578">COLUMN_PROPID</span></span>|<span data-ttu-id="52743-579">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-579">Int64</span></span>|  
|<span data-ttu-id="52743-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="52743-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="52743-581">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-581">Int64</span></span>|  
|<span data-ttu-id="52743-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="52743-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="52743-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-583">Boolean</span></span>|  
|<span data-ttu-id="52743-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="52743-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="52743-585">String</span><span class="sxs-lookup"><span data-stu-id="52743-585">String</span></span>|  
|<span data-ttu-id="52743-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="52743-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="52743-587">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-587">Int64</span></span>|  
|<span data-ttu-id="52743-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="52743-588">IS_NULLABLE</span></span>|<span data-ttu-id="52743-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-589">Boolean</span></span>|  
|<span data-ttu-id="52743-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="52743-590">DATA_TYPE</span></span>|<span data-ttu-id="52743-591">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-591">Int32</span></span>|  
|<span data-ttu-id="52743-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="52743-592">TYPE_GUID</span></span>|<span data-ttu-id="52743-593">Guid</span><span class="sxs-lookup"><span data-stu-id="52743-593">Guid</span></span>|  
|<span data-ttu-id="52743-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="52743-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="52743-595">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-595">Int64</span></span>|  
|<span data-ttu-id="52743-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="52743-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="52743-597">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-597">Int64</span></span>|  
|<span data-ttu-id="52743-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="52743-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="52743-599">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-599">Int32</span></span>|  
|<span data-ttu-id="52743-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="52743-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="52743-601">Int16</span><span class="sxs-lookup"><span data-stu-id="52743-601">Int16</span></span>|  
|<span data-ttu-id="52743-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="52743-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="52743-603">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-603">Int64</span></span>|  
|<span data-ttu-id="52743-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="52743-605">String</span><span class="sxs-lookup"><span data-stu-id="52743-605">String</span></span>|  
|<span data-ttu-id="52743-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="52743-607">String</span><span class="sxs-lookup"><span data-stu-id="52743-607">String</span></span>|  
|<span data-ttu-id="52743-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="52743-609">String</span><span class="sxs-lookup"><span data-stu-id="52743-609">String</span></span>|  
|<span data-ttu-id="52743-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="52743-611">String</span><span class="sxs-lookup"><span data-stu-id="52743-611">String</span></span>|  
|<span data-ttu-id="52743-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="52743-613">String</span><span class="sxs-lookup"><span data-stu-id="52743-613">String</span></span>|  
|<span data-ttu-id="52743-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-614">COLLATION_NAME</span></span>|<span data-ttu-id="52743-615">String</span><span class="sxs-lookup"><span data-stu-id="52743-615">String</span></span>|  
|<span data-ttu-id="52743-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="52743-617">String</span><span class="sxs-lookup"><span data-stu-id="52743-617">String</span></span>|  
|<span data-ttu-id="52743-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="52743-619">String</span><span class="sxs-lookup"><span data-stu-id="52743-619">String</span></span>|  
|<span data-ttu-id="52743-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-620">DOMAIN_NAME</span></span>|<span data-ttu-id="52743-621">String</span><span class="sxs-lookup"><span data-stu-id="52743-621">String</span></span>|  
|<span data-ttu-id="52743-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="52743-622">DESCRIPTION</span></span>|<span data-ttu-id="52743-623">String</span><span class="sxs-lookup"><span data-stu-id="52743-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="52743-624">程序</span><span class="sxs-lookup"><span data-stu-id="52743-624">Procedures</span></span>  
  
|<span data-ttu-id="52743-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="52743-625">ColumnName</span></span>|<span data-ttu-id="52743-626">DataType</span><span class="sxs-lookup"><span data-stu-id="52743-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="52743-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="52743-628">String</span><span class="sxs-lookup"><span data-stu-id="52743-628">String</span></span>|  
|<span data-ttu-id="52743-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="52743-630">String</span><span class="sxs-lookup"><span data-stu-id="52743-630">String</span></span>|  
|<span data-ttu-id="52743-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="52743-632">String</span><span class="sxs-lookup"><span data-stu-id="52743-632">String</span></span>|  
|<span data-ttu-id="52743-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="52743-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="52743-634">Int16</span><span class="sxs-lookup"><span data-stu-id="52743-634">Int16</span></span>|  
|<span data-ttu-id="52743-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="52743-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="52743-636">String</span><span class="sxs-lookup"><span data-stu-id="52743-636">String</span></span>|  
|<span data-ttu-id="52743-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="52743-637">DESCRIPTION</span></span>|<span data-ttu-id="52743-638">String</span><span class="sxs-lookup"><span data-stu-id="52743-638">String</span></span>|  
|<span data-ttu-id="52743-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="52743-639">DATE_CREATED</span></span>|<span data-ttu-id="52743-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="52743-640">DateTime</span></span>|  
|<span data-ttu-id="52743-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="52743-641">DATE_MODIFIED</span></span>|<span data-ttu-id="52743-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="52743-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="52743-643">檢視</span><span class="sxs-lookup"><span data-stu-id="52743-643">Views</span></span>  
  
|<span data-ttu-id="52743-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="52743-644">ColumnName</span></span>|<span data-ttu-id="52743-645">DataType</span><span class="sxs-lookup"><span data-stu-id="52743-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="52743-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-646">TABLE_CATALOG</span></span>|<span data-ttu-id="52743-647">String</span><span class="sxs-lookup"><span data-stu-id="52743-647">String</span></span>|  
|<span data-ttu-id="52743-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="52743-649">String</span><span class="sxs-lookup"><span data-stu-id="52743-649">String</span></span>|  
|<span data-ttu-id="52743-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-650">TABLE_NAME</span></span>|<span data-ttu-id="52743-651">String</span><span class="sxs-lookup"><span data-stu-id="52743-651">String</span></span>|  
|<span data-ttu-id="52743-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="52743-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="52743-653">String</span><span class="sxs-lookup"><span data-stu-id="52743-653">String</span></span>|  
|<span data-ttu-id="52743-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="52743-654">CHECK_OPTION</span></span>|<span data-ttu-id="52743-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-655">Boolean</span></span>|  
|<span data-ttu-id="52743-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="52743-656">IS_UPDATABLE</span></span>|<span data-ttu-id="52743-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-657">Boolean</span></span>|  
|<span data-ttu-id="52743-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="52743-658">DESCRIPTION</span></span>|<span data-ttu-id="52743-659">String</span><span class="sxs-lookup"><span data-stu-id="52743-659">String</span></span>|  
|<span data-ttu-id="52743-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="52743-660">DATE_CREATED</span></span>|<span data-ttu-id="52743-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="52743-661">DateTime</span></span>|  
|<span data-ttu-id="52743-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="52743-662">DATE_MODIFIED</span></span>|<span data-ttu-id="52743-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="52743-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="52743-664">索引</span><span class="sxs-lookup"><span data-stu-id="52743-664">Indexes</span></span>  
  
|<span data-ttu-id="52743-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="52743-665">ColumnName</span></span>|<span data-ttu-id="52743-666">DataType</span><span class="sxs-lookup"><span data-stu-id="52743-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="52743-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-667">TABLE_CATALOG</span></span>|<span data-ttu-id="52743-668">String</span><span class="sxs-lookup"><span data-stu-id="52743-668">String</span></span>|  
|<span data-ttu-id="52743-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="52743-670">String</span><span class="sxs-lookup"><span data-stu-id="52743-670">String</span></span>|  
|<span data-ttu-id="52743-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-671">TABLE_NAME</span></span>|<span data-ttu-id="52743-672">String</span><span class="sxs-lookup"><span data-stu-id="52743-672">String</span></span>|  
|<span data-ttu-id="52743-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="52743-673">INDEX_CATALOG</span></span>|<span data-ttu-id="52743-674">String</span><span class="sxs-lookup"><span data-stu-id="52743-674">String</span></span>|  
|<span data-ttu-id="52743-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="52743-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="52743-676">String</span><span class="sxs-lookup"><span data-stu-id="52743-676">String</span></span>|  
|<span data-ttu-id="52743-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-677">INDEX_NAME</span></span>|<span data-ttu-id="52743-678">String</span><span class="sxs-lookup"><span data-stu-id="52743-678">String</span></span>|  
|<span data-ttu-id="52743-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="52743-679">PRIMARY_KEY</span></span>|<span data-ttu-id="52743-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-680">Boolean</span></span>|  
|<span data-ttu-id="52743-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="52743-681">UNIQUE</span></span>|<span data-ttu-id="52743-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-682">Boolean</span></span>|  
|<span data-ttu-id="52743-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="52743-683">CLUSTERED</span></span>|<span data-ttu-id="52743-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-684">Boolean</span></span>|  
|<span data-ttu-id="52743-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="52743-685">TYPE</span></span>|<span data-ttu-id="52743-686">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-686">Int32</span></span>|  
|<span data-ttu-id="52743-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="52743-687">FILL_FACTOR</span></span>|<span data-ttu-id="52743-688">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-688">Int32</span></span>|  
|<span data-ttu-id="52743-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="52743-689">INITIAL_SIZE</span></span>|<span data-ttu-id="52743-690">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-690">Int32</span></span>|  
|<span data-ttu-id="52743-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="52743-691">NULLS</span></span>|<span data-ttu-id="52743-692">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-692">Int32</span></span>|  
|<span data-ttu-id="52743-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="52743-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="52743-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-694">Boolean</span></span>|  
|<span data-ttu-id="52743-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="52743-695">AUTO_UPDATE</span></span>|<span data-ttu-id="52743-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-696">Boolean</span></span>|  
|<span data-ttu-id="52743-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="52743-697">NULL_COLLATION</span></span>|<span data-ttu-id="52743-698">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-698">Int32</span></span>|  
|<span data-ttu-id="52743-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="52743-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="52743-700">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-700">Int64</span></span>|  
|<span data-ttu-id="52743-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="52743-701">COLUMN_NAME</span></span>|<span data-ttu-id="52743-702">String</span><span class="sxs-lookup"><span data-stu-id="52743-702">String</span></span>|  
|<span data-ttu-id="52743-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="52743-703">COLUMN_GUID</span></span>|<span data-ttu-id="52743-704">Guid</span><span class="sxs-lookup"><span data-stu-id="52743-704">Guid</span></span>|  
|<span data-ttu-id="52743-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="52743-705">COLUMN_PROPID</span></span>|<span data-ttu-id="52743-706">Int64</span><span class="sxs-lookup"><span data-stu-id="52743-706">Int64</span></span>|  
|<span data-ttu-id="52743-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="52743-707">COLLATION</span></span>|<span data-ttu-id="52743-708">Int16</span><span class="sxs-lookup"><span data-stu-id="52743-708">Int16</span></span>|  
|<span data-ttu-id="52743-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="52743-709">CARDINALITY</span></span>|<span data-ttu-id="52743-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="52743-710">Decimal</span></span>|  
|<span data-ttu-id="52743-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="52743-711">PAGES</span></span>|<span data-ttu-id="52743-712">Int32</span><span class="sxs-lookup"><span data-stu-id="52743-712">Int32</span></span>|  
|<span data-ttu-id="52743-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="52743-713">FILTER_CONDITION</span></span>|<span data-ttu-id="52743-714">String</span><span class="sxs-lookup"><span data-stu-id="52743-714">String</span></span>|  
|<span data-ttu-id="52743-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="52743-715">INTEGRATED</span></span>|<span data-ttu-id="52743-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="52743-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52743-717">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52743-717">See also</span></span>

- [<span data-ttu-id="52743-718">ADO.NET Managed 提供者和DataSet開發人員中心</span><span class="sxs-lookup"><span data-stu-id="52743-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
