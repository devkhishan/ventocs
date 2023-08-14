#Internship Documentation

---

# **Blockchain Comment System Integration Documentation**

## **1. Smart Contract Deployment**

**Method Name: *deployContract***

**Description:** This method deploys the CommentSystem smart contract to the Ethereum blockchain.

**Parameters:** None

**Returns:** The deployed contract address

To deploy the CommentSystem smart contract, use the **deployContract** method. This method does not require any parameters. It will return the address of the deployed contract on the Ethereum blockchain.

```
const deployContract = async () => {
  const contract = new web3.eth.Contract(CommentSystemABI);
  const deployTx = contract.deploy({ data: CommentSystemBytecode });
  const deployReceipt = await deployTx.send({ from: accounts[0], gas: '1000000' });
  return deployReceipt.options.address; 
}; 
```

## **2. Adding a Comment**

**Method Name: *addComment***

**Description:** This method allows users to add a new top-level comment.

**Parameters:**

 - user
 - content
**Returns:** The transaction hash of the comment addition

To add a new top-level comment, use the **addComment** method. Provide the user's Ethereum address and the content of the comment. The method will add the comment to the blockchain and return the transaction hash for the addition.

```
const addComment = async (user, content) => {
  const contract = new web3.eth.Contract(CommentSystemABI, contractAddress);
  const tx = contract.methods.addComment(content); 
  const txReceipt = await tx.send({ from: user, gas: '1000000' }); 
  return txReceipt.transactionHash; 
}; 
```

## **3. Adding a Reply**

**Method Name: *addReply***

**Description:** This method allows users to add a reply to an existing comment.

**Parameters:**

 - user
 - commentId
 - content
**Returns:** The transaction hash of the reply addition

To add a reply to an existing comment, use the **addReply** method. Provide the user's Ethereum address, the ID of the parent comment, and the content of the reply. The method will add the reply to the blockchain and return the transaction hash for the addition.

```
const addReply = async (user, commentId, content) => { 
  const contract = new web3.eth.Contract(CommentSystemABI, contractAddress); 
  const tx = contract.methods.addReply(commentId, content); 
  const txReceipt = await tx.send({ from: user, gas: '1000000' }); 
  return txReceipt.transactionHash; 
}; 
```

## **4. Getting Comments**

**Method Name: *getComments***

**Description:** This method retrieves a list of top-level comments.

**Parameters:** None

**Returns:** An array of comment objects

To retrieve a list of top-level comments, use the **getComments** method. This method does not require any parameters. It will return an array of comment objects representing the top-level comments in the system.

```
const getComments = async () => { 
  const contract = new web3.eth.Contract(CommentSystemABI, contractAddress); 
  const comments = await contract.methods.getComments().call(); 
  return comments; 
}; 
```

## **5. Voting on a Comment or Reply**

**Method Name: *voteOnComment***

**Description:** This method allows users to vote on a comment or reply.

**Parameters:**

 - user
 - itemId
 - voteType
**Returns:** The transaction hash of the vote transaction

To vote on a comment or reply, use the **voteOnComment** method. Provide the user's Ethereum address, the ID of the comment or reply, and the type of vote ("up" or "down"). The method will register the vote on the blockchain and return the transaction hash for the vote.

```
const voteOnComment = async (user, itemId, voteType) => { 
  const contract = new web3.eth.Contract(CommentSystemABI, contractAddress); 
  const tx = contract.methods.voteOnComment(itemId, voteType); 
  const txReceipt = await tx.send({ from: user, gas: '1000000' }); 
  return txReceipt.transactionHash; 
}; 
```

## **6. Deleting a Comment or Reply**

**Method Name: *deleteItem***

**Description:** This method allows users to delete their own comments or replies.

**Parameters:**

 - user
 - itemId
**Returns:** The transaction hash of the deletion transaction

To delete a comment or reply, use the **deleteItem** method. Provide the user's Ethereum address and the ID of the comment or reply. The method will delete the item from the blockchain and return the transaction hash for the deletion.

```
const deleteItem = async (user, itemId) => { 
  const contract = new web3.eth.Contract(CommentSystemABI, contractAddress); 
  const tx = contract.methods.deleteItem(itemId); 
  const txReceipt = await tx.send({ from: user, gas: '1000000' }); 
  return txReceipt.transactionHash; 
}; 
```

## **7. Reporting a Comment or Reply**

**Method Name: *reportItem***

**Description:** This method allows users to report inappropriate comments or replies.

**Parameters:**

 - user
 - itemId
**Returns:** The transaction hash of the report transaction

To report a comment or reply as inappropriate, use the **reportItem** method. Provide the user's Ethereum address and the ID of the comment or reply. The method will register the report on the blockchain and return the transaction hash for the report.

```
const reportItem = async (user, itemId) => { 
  const contract = new web3.eth.Contract(CommentSystemABI, contractAddress); 
  const tx = contract.methods.reportItem(itemId); 
  const txReceipt = await tx.send({ from: user, gas: '1000000' }); 
  return txReceipt.transactionHash; 
}; 
```

## **8. Marking a Comment or Reply as Helpful**

**Method Name: *markItemAsHelpful***

**Description:** This method allows users to mark a comment or reply as helpful.

**Parameters:**

 - user
 - itemId
**Returns:** The transaction hash of the marking transaction

To mark a comment or reply as helpful, use the **markItemAsHelpful** method. Provide the user's Ethereum address and the ID of the comment or reply. The method will register the helpful mark on the blockchain and return the transaction hash for the marking.

```
const markItemAsHelpful = async (user, itemId) => { 
  const contract = new web3.eth.Contract(CommentSystemABI, contractAddress); 
  const tx = contract.methods.markItemAsHelpful(itemId); 
  const txReceipt = await tx.send({ from: user, gas: '1000000' }); 
  return txReceipt.transactionHash; 
}; 
```

## **9. Pinning a Comment or Reply**

**Method Name: *pinItem***

**Description:** This method allows moderators to pin a comment or reply to the top.

**Parameters:**

 - moderator
 - itemId
**Returns:** The transaction hash of the pinning transaction

To pin a comment or reply to the top, use the **pinItem** method. Provide the moderator's Ethereum address and the ID of the comment or reply. The method will pin the item to the top and return the transaction hash for the pinning.

```
const pinItem = async (moderator, itemId) => { 
  const contract = new web3.eth.Contract(CommentSystemABI, contractAddress); 
  const tx = contract.methods.pinItem(itemId); 
  const txReceipt = await tx.send({ from: moderator, gas: '1000000' }); 
  return txReceipt.transactionHash; 
};
```

## **10. User Reputation**

**Method Name: *getUserReputation***

**Description:** This method retrieves the reputation score of a user.

**Parameters:**

 - user
**Returns:** The reputation score of the user

To retrieve the reputation score of a user, use the **getUserReputation** method. Provide the user's Ethereum address. The method will return the reputation score of the user.

```
const getUserReputation = async (user) => { 
  const contract = new web3.eth.Contract(CommentSystemABI, contractAddress); 
  const reputation = await contract.methods.getUserReputation(user).call(); 
  return reputation; 
}; 
```

## **11. Trending Comments**

**Method Name: *getTrendingComments***

**Description:** This method retrieves a list of trending comments.

**Parameters:** None

**Returns:** An array of comment objects

To retrieve a list of trending comments, use the **getTrendingComments** method. This method does not require any parameters. It will return an array of comment objects representing the trending comments in the system.

```
const getTrendingComments = async () => { 
  const contract = new web3.eth.Contract(CommentSystemABI, contractAddress); 
  const trendingComments = await contract.methods.getTrendingComments().call(); 
  return trendingComments; 
}; 
```

## **12. Nested Thread Structure**

**Method Name: *getCommentThread***

**Description:** This method retrieves the nested thread structure of a comment.

**Parameters:**

 - commentId
**Returns:** A nested thread structure object

To retrieve the nested thread structure of a comment, use the **getCommentThread** method. Provide the ID of the comment. The method will return a nested thread structure object representing the comment and its replies.

```
const getCommentThread = async (commentId) => { 
  const contract = new web3.eth.Contract(CommentSystemABI, contractAddress); 
  const commentThread = await contract.methods.getCommentThread(commentId).call(); 
  return commentThread; 
}; 
```

## **13. Moderation Tools**

**Method Name: *moderateItem***

**Description:** This method allows moderators to moderate comments or replies.

**Parameters:**

 - moderator
 - itemId
 - action
**Returns:** The transaction hash of the moderation transaction

To moderate a comment or reply, use the **moderateItem** method. Provide the moderator's Ethereum address, the ID of the comment or reply, and the moderation action ("approve" or "reject"). The method will execute the moderation action on the blockchain and return the transaction hash for the moderation.

```
const moderateItem = async (moderator, itemId, action) => { 
  const contract = new web3.eth.Contract(CommentSystemABI, contractAddress); 
  const tx = contract.methods.moderateItem(itemId, action); 
  const txReceipt = await tx.send({ from: moderator, gas: '1000000' }); 
  return txReceipt.transactionHash; 
};
```

## **14. User Reputation**

**Method Name: *getUserReputation***

**Description:** This method retrieves the reputation score of a user.

**Parameters:**

 - user
**Returns:** The reputation score of the user

The **getUserReputation** method allows you to retrieve the reputation score of a specific user. Provide the user's Ethereum address, and the method will return the user's reputation score based on their contributions and interactions within the comment system.

## **15. Trending Comments**

**Method Name: *getTrendingComments***

**Description:** This method retrieves the currently trending comments.

**Parameters:** None

**Returns:** An array of trending comment objects

To fetch the comments that are currently trending, use the **getTrendingComments** method. This method does not require any parameters. It will return an array of comment objects that are receiving a high number of votes, replies, or other engagement metrics, indicating their popularity.
