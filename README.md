# before-delet
Album
Moralis.Cloud.beforeDelete("Album", async (request) => {
  const query = new Moralis.Query("Photo");
  query.equalTo("album", request.object);
  const count = await query.count({ useMasterKey: true });
  if (count > 0) {
    throw "Can't delete album if it still has photos.";
  }
});
