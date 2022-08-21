# Smart Contract Break-Down

#### Description

This particular approach for the smart contract aims to open up the investing solution to all $AVAN Holders so that they can invest, vote, and maintain the stability of the token. Investors are not allowed to fill more than 5% of the total pool value for each address and each pool, preventing whale power on DAO voting and "preventing manipulation" by giving investors equal power.

#### New Proposal

We were able to examine how investing suggestions are made in the smart contract coding we provided:

```solidity
function createProposal(uint256 _end, string calldata _proposal) public onlyOwner{
```

#### DAO voting

To ensure that investors have complete power over their investment decisions, we have "3" DAO voting for each pool. code line illustration

<pre class="language-solidity"><code class="lang-solidity">function vote(uint256 _proposal, bool _YesOrNo) public {
    struct Vote {
        uint256 end;
        string proposal;
        uint256 powerYes;
        uint256 powerNo;
<strong>    }
</strong>    mapping(uint256 => Vote) proposals; //id to proposal
    mapping(address => mapping(uint256 => bool)) hasVoted; //if user has voted on 
proposal
    uint256 runningProposals; // latest proposal id</code></pre>

#### Fund Raising

To keep records accurate and to send annual returns to the same address in the future, all are transferred via smart contracts:

```solidity
function getInvestedIdsOf(address _add) public view returns(uint256[] memory _ids) {
        uint256 count = 0;
            for(uint256 i; i < runningCount-1; i++) {
            if(FundPool(FundList[i]).tokensOf(_add) > 0){
                _ids[count] = i;
                count++;
            }
        }
    }
```
