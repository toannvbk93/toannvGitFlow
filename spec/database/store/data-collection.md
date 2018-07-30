# Data Collection

## Schema
```
{
  _id : ObjectID,
  sourceType: String,
  createAt: Date,
  updateAt: Date,
  syncedAt: Date,
  data: {
    _id: ObjectIDj,
    updateAt: Date,
    isActive: boolean,
    title: String,
    kana: String,
    explanation: String,
    imagePath: String,
    targetRole: String,
    publishDate: Date
    additionalInfo: {
      mddc: {
        dataId: String,
        genreCode: String,
        r18Rating: String
      },
      ccc: {
        genreCode : [],
        productUrl : {
          stockSearchUrl: String;
          relatedbookSearchUrl: String
        }
      }
    },
    contents: [
      {
        _id: ObjectID,
        createAt: Date,
        updateAt: Date,
        isActive: boolean,
        title: String,
        kana: String,
        publishStartDateTime: Date,
        publishEndDateTime: Date,
        description: String,
        imagePath: String,
        targetrole: String[],
        commonCode: {
          JDCN: String,
          IBAN: String,
          JAN: String,
        },
        additionalInfo: {
          mddc: {
            price: Number,
            downloadLimit: Number,
            fireSize: Number,
            master: Number,
            permitId: String,
            format: String,
            permitStart: String,
            permitEnd: String,
            jdcn: String,
            publisherContentCode: String,
            magazineNumber: Date,
            openDateTime: Date,
          }
        }
      }
    ],
    author: {
      _id: ObjectId,
      createAt: Date,
      updateAt: Date,
      isActive: Boolean,
      name: String,
      kana: String,
      imagePath: String,
      additionalInfo: {
        mddc: {
          authorId: String
        }
      }
    },
    publisher: {
      _id: ObjectId,
      createAt: Date,
      updateAt: Date,
      isActive: Boolean,
      name: String,
      kana: String,
      additionalInfo: {
        mddc: {
          publisherId: String,
          reportName: String,
        },
        ccc: {
          publisherId: String,
          paymentClientId: String
        }
      }
    }
  }
}
``'
