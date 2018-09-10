## Creating Smart Contracts with Truffle

### Solidity Account ONLY syntax

Example

```solidity
pragma solidity ^0.4.0;

contract SimpleContract(){

	string word = "Initial Word"

	address issuer;

	// *** consstructor ...
	function Simplecontract(){
		issue = msg.sender;
	}


	modifier ifIssuer(){
		// *** if not issuer then
		// *** throw exception else continue ...
		if(issuer != msg.sender){
			throw;
		}
		else
		{
			_;
		}
	}


	function setWord(string newWord) ifIssuer returns(string){
		word = newWord;
		return "changed by creator";
	}
}

```

