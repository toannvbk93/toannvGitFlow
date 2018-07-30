# Data Collection

## Schema
```
{
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
```
