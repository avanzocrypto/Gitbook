# Copy of Smart Contract Break-Down

#### Description

This specific approach for the smart contract targets to make investing solution open to all $AVAN Holders to invest, vote and keep stabilizing the coin, Investors are not allowed to fill more than 5% of total pool value for each address and each pool, preventing whale power on DAO voting, giving power to investors equally "preventing manipulation".

#### New Proposal

In our provided smart contract coding we could see how investing proposals are created:

```solidity
function createProposal(uint256 _end, string calldata _proposal) public onlyOwner{
```

#### DAO voting

we got "3" DAO voting for each pool to make sure that investors have full control over their investment decisions code line example:

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
    uint256 runningProposals; // latest proposal id
</code></pre>

#### Fund Raising

All funds are being transacted using the smart contract to keep records tight to address and also to send annual returns later on to same address:

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















