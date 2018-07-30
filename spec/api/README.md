# API reference

## Guest API List \(GraphQL\)

| Endpoint | Function | Description |
| --- | --- | --- |
| /gapi/guest | [lamchinsu](guest/store/gapi-guest-search.md) | Searches the titles by keywords and retrieves the results as a list of titles. |
| /gapi/guest | [getBookListByCategoryId](guest/store/gapi-guest-getbooklistbycategoryid.md) | Retrieves a list of books corresponding to the store categories. |
| /gapi/guest | [getBookListByTitleId](guest/store/gapi-guest-getbooklistbytitleid.md) | Retrieves a list of books corresponding to the title. |
| /gapi/guest | [getBook](guest/store/gapi-guest-getbook.md) | Retrieves information of a book. 
| /gapi/guest | [getBookDownloadInfo](guest/store/gapi-guest-getbookdownloadinfo.md) | Retrieves the required information to download/view books. |
| /gapi/guest | [getStoreCategories](guest/store/gapi-guest-getstorecategories.md) | Retrieves all store categories. \(Argument candidates: top, recommend, ranking and orderby\) |
| /gapi/guest | [getSuggestWords](guest/store/gapi-guest-getsuggestwords.md) | Retrieves suggest words corresponding to an arbitrary word. |

## Guest API List \(AppSync\)

| Endpoint | Function | Description |
| --- | --- | --- |
| /graphql | [getNoticeList](guest/appsync/graphql-getnoticelist-guestapi.md) | Retrieves a list of notices. |
| /graphql | [getAppVersionInfo](guest/appsync/graphql-getappversioninfo-guestapi.md) | Retrieves the latest version information (force update) of the app. |
| /graphql | [getAppConfig](guest/appsync/graphql-getappconfig-guestapi.md) | Retrieves the system setting information such as external site URL information. |

## Member Web Endpoint List

| Endpoint | Type | Description |  |
| --- | --- | --- | --- |
| /member/login | [GET](member/store/member-login.md) | Authentication | Logs in to the store API server and generates a session. |
| /member/logout | [POST](member/store/member-logout.md) | Authentication | Get application latest version |

## Member API List \(REST\)

| Endpoint | Type | Description |
| --- | --- | --- |
| /api/member/token | [POST](member/store/api-member-token.md) | Get token |

## Member API List \(GraphQL\)

| Endpoint | Function | Description |
| --- | --- | --- |
| /gapi/member | [login](member/store/gapi-member-login.md) | Login to the store API server. |
| /gapi/member | [logout](member/store/gapi-member-logout.md) | Logout from the store API server |
| /gapi/member | [renewToken](member/store/gapi-member-renewtoken.md) | Re-retrieves the custom token necessary for using the API. |
| /gapi/member | [search](member/store/gapi-member-search.md) | Searches the titles by keywords and retrieves the results as a list of titles. |
| /gapi/member | [getBookListByCategoryId](member/store/gapi-member-getbooklistbycategoryid.md) | Retrieves a list of books corresponding to the store categories. |
| /gapi/member | [getBookListByTitleId](member/store/gapi-member-getbooklistbytitleid.md) | Retrieves a list of books corresponding to the title. Or retrieves a list of books from book ID list. |
| /gapi/member | [getBook](member/store/gapi-member-getbook.md) | Retrieves information of a book in the title. |
| /gapi/member | [getBookDownloadInfo](member/store/gapi-member-getbookdownloadinfo.md) | Retrieves the required information to download/view books. |
| /gapi/member | [getStoreCategories](member/store/gapi-member-getstorecategories.md) | Retrieves all store categories. \(Argument candidates: top, recommend, ranking and orderby\) |
| /gapi/member | [getSuggestWords](member/store/gapi-member-getsuggestwords.md) | Suggest Word |

## Member API List \(AppSync\)

| Endpoint | Function | Description |
| --- | --- | --- |
| /graphql | [getNoticeList](member/appsync/graphql-getnoticelist-memberapi.md) | Retrieves a list of notices. |
| /graphql | [getAppVersionInfo](member/appsync/graphql-getappversioninfo-memberapi.md) | Retrieves the latest version information \(force update\) of the app. |
| /graphql | [getAppConfig](member/appsync/graphql-getappconfig-memberapi.md) | Retrieves the system setting information such as external site URL information. |
| /graphql | [getFavoriteList](member/appsync/graphql-getfavoritelist.md) | Retrieves a list of titles in my list. |
| /graphql | [addFavorite](member/appsync/graphql-addfavorite.md) | Adds a specific title to my list. |
| /graphql | [deleteFavorite](member/appsync/graphql-deletefavorite.md) | Deletes a specific title from my list. |
| /graphql | [getUserSetting](member/appsync/graphql-getusersetting.md) | Retrieves user-specific setting information that needs to be synchronized between the web or devices. |
| /graphql | [updateUserSetting](member/appsync/graphql-updateusersetting.md) | Updates user-specific setting information. |
| /graphql | [getLoginDeviceList](member/appsync/graphql-getlogindevicelist.md) | Retrieves a list of currently logged-in devices. |
| /graphql | [addLoginDevice](member/appsync/graphql-addlogindevice.md) | Adds a device information as currently logged in device.\(This API will not be affected by the number limit of devices.\) |
| /graphql | [deleteLoginDevice](member/appsync/graphql-deletelogindevice.md) | Deletes specific device information from currently logged in devices. |

## Admin API List \(POST\)

| Endpoint | Type | Description |  |
| --- | --- | --- |
| /admin/login | [GET](admin/store/admin-login.md) | Authentication | Logs in to the store API server and generates a session. |
| /admin/logout | [POST](admin/store/admin-logout.md) | Authentication | Get application latest version |

## Admin API List \(POST\)

| Endpoint | Type | Description |
| --- | --- | --- |
| /api/admin/token | [POST](admin/store/api-admin-token.md) | Get token |

## Admin API List \(GraphQL\)

| Endpoint | Function | Description |
| --- | --- | --- |
| /gapi/admin | [login](admin/store/gapi-admin-login.md) | Logs in to the store API server for administrators |
| /gapi/admin | [logout](https://github.com/lunascape/tp-store-service/tree/512ef7238eff8134b60550d4d5447dd59c3b4bf0/admin/store/gapi-admin-logout.md) | Logs out from the store API server for administrators |
| /gapi/admin | [renewToken](admin/store/gapi-admin-renewtoken.md) | Re-retrieves the custom token necessary for using the API for administrators. |
| /gapi/admin | [getTitleList](admin/store/gapi-admin-gettitlelist.md) | Retrieves a list of titles under specified conditions. |
| /gapi/admin | [getTitle](admin/store/gapi-admin-gettitle.md) | Retrieves title information. |
| /gapi/admin | [addTitle](admin/store/gapi-admin-addtitle.md) | Adds title information. |
| /gapi/admin | [updateTitle](admin/store/gapi-admin-updatetitle.md) | Updates title information. \(Only store-specific information can be updated\) |
| /gapi/admin | [deleteTitle](admin/store/gapi-admin-deletetitle.md) | Physically deletes title information. \(This is for emergency use. Please use update when deleting logically\) |
| /gapi/admin | [getBook](admin/store/gapi-admin-getbook.md) | Retrieves book information. |
| /gapi/admin | [addBook](admin/store/gapi-admin-addbook.md) | Adds book information. |
| /gapi/admin | [updateBook](admin/store/gapi-admin-updatebook.md) | Updates book information. Physically deletes title information. |
| /gapi/admin | [deleteBook](admin/store/gapi-admin-deletebook.md) | Deletes book information. \(This is for emergency use. Please use update when deleting logically\) |
| /gapi/admin | [getDCCategories](admin/store/gapi-admin-getdccategories.md) | Retrieves all DC category information. |
| /gapi/admin | [addDCCategory](admin/store/gapi-admin-adddccategory.md) | Adds DC category information. |
| /gapi/admin | [updateDCCategory](admin/store/gapi-admin-updatedccategory.md) | Updates DC category information. |
| /gapi/admin | [deleteDCategory](https://github.com/lunascape/tp-store-service/tree/31d58ae4aa097f07f6b2c77383aeaf092df8fc48/docs/spec/api/admin/store/gapi-admin-deleteDCategory.md) | Deletes DC category information. |
| /gapi/admin | [getStoreCategory](admin/store/gapi-admin-getstorecategory.md) | Store category includes top category, recommendation information, ranking information. |
| /gapi/admin | [addStoreCategory](admin/store/gapi-admin-addstorecategory.md) | Adds store category information. |
| /gapi/admin | [updateStoreCategory](admin/store/gapi-admin-updatestorecategory.md) | Updates store category information. |
| /gapi/admin | [deleteStoreCategory](admin/store/gapi-admin-deletestorecategory.md) | Deletes store category information. |
| /gapi/admin | [getAdminUserList](admin/store/gapi-admin-getadminuserlist.md) | Searches admin users and retrieves the list. |
| /gapi/admin | [getAdminUser](admin/store/gapi-admin-getadminuser.md) | Retrieves admin user information. |
| /gapi/admin | [addAdminUser](admin/store/gapi-admin-addadminuser.md) | Adds admin user information. |
| /gapi/admin | [updateAdminUser](admin/store/gapi-admin-updateadminuser.md) | Updates admin user information. |
| /gapi/admin | [deleteAdminUser](admin/store/gapi-admin-deleteadminuser.md) | Deletes admin user information. |

## Admin API List \(AppSync\)

| Endpoint | Type | Description |
| --- | --- | --- |
| /graphql | [getNoticeList](admin/appsync/admin-api-appsync-getnoticelist.md) | Retrieves a list of all notice information including non-public information. |
| /graphql | [getNotice](admin/appsync/admin-api-appsync-getnotice.md) | Retrieves notice information. |
| /graphql | [addNotice](admin/appsync/admin-api-appsync-addnotice.md) | Adds notice information. |
| /graphql | [updateNotice](admin/appsync/admin-api-appsync-updatenotice.md) | Updates specific notice information. |
| /graphql | [deleteNotice](admin/appsync/admin-api-appsync-deletenotice.md) | Deletes specific notice information. |
| /graphql | [getAppConfigList](admin/appsync/admin-api-appsync-getconfiglist.md) | Retrieves a list of all system setting information. |
| /graphql | [getConfig](admin/appsync/admin-api-appsync-getconfig.md) | Retrieves system setting information. |
| /graphql | [addConfig](admin/appsync/admin-api-appsync-addconfig.md) | Adds system setting information. |
| /graphql | [setConfig](admin/appsync/admin-api-appsync-updateconfig.md) | Updates system setting information. |
| /graphql | [deleteConfig](admin/appsync/admin-api-appsync-deleteconfig.md) | Deletes system setting information. |

