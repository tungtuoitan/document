# nghiên cứu mua GPT trên window để học C#

# **Task 100**

- không chỉ Pending, mà non-Pending cũng xóa được

- nguyên nhân re-render ?
- logic hiện tại?
- có nhiều delete button ?

<!-- vậy, có tất cả bao nhiêu ?? -->

- khi mở nhiều tab, và click delete, thì sẽ refresh toàn bộ tab phải không ??
- tóm tắt task trên itsm ?

hiện trạng: sau khi xóa **Pending** Audit thì các list trên các tab không bị refresh
expect:

- sau khi click thì phải refresh,
- list nào cần update thì mới update

- useQCProdSKUGridHelper
<!-- chứa hàm xử lí click View Audit History -->

View Audit History click

<!-- setSkuHistorySelected(params.row.sku);
setPopAnchorEl(event.currentTarget); -->

-- Remove Report Click --

 <!-- onClickHandlerDelete(e, selectedId) -->

initializationPopoverBox( IInitializationPopoverBox )

IInitializationPopoverBox.okCallback()

# **luồng chạy của data**

<!-- - tại tab Search -->

# **sơ đồ component**

QCProdSKUGrid
<!-- (lấy gridColumns từ useQCProdSKUGridHelper) -->

"/qc" -- (QCContainerLazy) -- (QCContainerRoot) -- (QCProviders) + (QCContainer) -- QCTabs --
-- (TabsContainer) + _SearchTabContainer,AuditTabContainer,ReportsTabContainer_ --
-- BoxTab (item trên header) + TabPanel(SearchTabContainer) (body, @@ )

-- \*\*SearchTabContainer (nơi bắt đầu data) -- TabBodyContainer(SearchTabWithFilter, QcSearchTabFilterDrawer(đây là drawer, khi click filter thì nó hiển thị))

-- SearchTabWithFilter(QCProdOrderGrid)

-- _QCProdOrderGrid_ (đây là List của Search, có màu vàng)

<!-- -- ProductOrderReferenceDetail (là right of item) -->

<!-- -- useQCProdOrderGridHelper (nơi data của grid bắt đầu) -->

# =========================================AuditProdOrder==========================================

# **về QCProdOrderGrid**

- gridColumnProdOrderReference (đại diện cho các columns)
 <!-- [
  {
    field: 'id',
    headerName: 'ID',
    width: 100,
  },
  {
    field: 'name',
    headerName: 'Name',
    width: 200,
  },QCProdSKUGrid
  // Các cột khác...
]; -->

- View Detail2 Button và hàm click
  onClickHandlerQCProdOrderView

-

# **data truyền vào List (QCProdOrderGrid)**

- bắt dầu
  loadQCAuditProdOrders (thuộc useQCAuditLoaders) -- _getQCAuditPage_(đây là hàm fetch data)

useQCSearchStore()
setQCProdOrderPage (để lưu data trong qcProdOrderPage)
-- qcProdOrderPage (chứa toàn bộ 100 row, stt của page, số lượng row...)
-- qcProdOrderPage?.records

#  =========================================AuditProdOrder==========================================

- setQCAuditProdOrderTabs (hàm này để mở thêm 1 list prod, tương ứng với 1 prod order )

- AuditProdOrder
-  (là ProdOrder Grid chính ,tức list các prod)

- gridColumns (đại diện cho các columns)

# dòng chảy data

getQCAuditDetails (đây là hàm fetch)

(4 hàm này là đầu nguồn)

1.getProdSKUDataFromTabById (hàm này chưa dùng)

2.loadProductionOrderRefByTabIndex (trong useEffect)

<!-- hàm này chạy, và khi online thì sẽ chạy setQCAuditDetailPage, khi offline thì chạy getProdSKUDataFromTabByIndex -->
<!-- (hàm này chạy khi khởi tạo Grid, và mỗi khi reloadProdSKUGrid thay đổi, và trong code thì reloadProdSKUGrid cũng k thay đổi, tức hàm nfay chỉ chạy khi khởi tạo ) -->
<!-- đã check, và khi thao tác thì hàm này k chạy lại -->

3.getProdSKUDataFromTabByIndex

<!-- mỗi khi click vào tab, thì nó sẽ chạy -->

4.loadQCAuditDetails

<!-- chạy mỗi lần mở click để mở ra 1 order
chạy mỗi khi xóa Pending -->

qcAuditDetailPage?.records

# **phân tích 1**

## Khi click tạo ra tab mới

> > > > > > loadProductionOrderRefByTabIndex -- loadQCAuditDetails

## khi click vào tab

getProdSKUDataFromTabByIndex
loadProductionOrderRefByTabIndex
getProdSKUDataFromTabByIndex

## khi tick chọn (nothin happen)

## khi chuyển sang Pending

loadQCAuditDetails

## khi click mở popup (để xóa pending) nothin happen

## khi xóa pending
onClickHandlerDelete >>
initializationPopoverBox >>
okCallback() >>
db.getQCAuditHeadersByQCAuditHeaderId.then() >>
db.deleteQCAuditHeader.then() >>
refreshAllProdOrderSKUTabs >> updateProdOrderSKUGrid >> loadQCAuditDetails >> ..


# **trace**
- lí do:
data truyền vào 4444 undefined
>> do db.getQCAuditHeadersByQCAuditHeaderId trả về undefined 
>> do this.qcAuditHeaders.where('id').equals(qcAuditHeaderId).first(); trả về undefined
>> do không có row tương ứng trong table qcAuditHeaders

qcAuditHeaders: là bảng liên quan trong QCDatabase


# **Phân tích render QCProdSKUGrid**

SearchTabs (truyền vào AuditProdOrder) 
 --

setQCAuditDetailPage() --
QCProdSKUGrid

<!-- qcAuditDetailPage (chứa data list) -->
