# Encryption
For some apps, having end-to-end encryption and user privacy is one of the top priorities. An encryption extension can be added to AppFriends by providing a implementation of `AFEncryptionDelegate`.
An example of `AFEncryptionDelegate` implementation can be found [here](https://gist.github.com/laeroah/aeabc9bfd7e96a8ab5e6b20d979e575d).

In the sample implementation we used [Virgil](virgilsecurity.com), which is encryption service provider. Please refer to [this article](https://medium.com/@haowang_81947/how-to-build-secure-chat-with-appfriends-and-virgil-f562683169e8) for details on how to using Virgil to secure AppFriends chat communication.
