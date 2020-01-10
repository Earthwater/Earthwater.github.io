---
layout: post
title:  "Some thinkings of differences between cryptography and system security"
date:   2018-05-17 14:05:21 +0800
tags: blogs
color: rgb(255,90,90)
cover: '../assets/test.png'
subtitle: 'Differences between cryptography and system security'
---
It seems like  there is a understanding gap among security researchers from cryptography and system security.
Well, from my perspective, i would like to make a metaphor to describe `my` understanding towards it.

Before that, i need to point out, what i mean system security area is that all related security areas except cryptography researchers are focused on.

Let's say there is a building, whose foundation is the cryptography, but there are a lot of other systems like elevator or electric system are system security areas. The foundation also consists of various aspects, e.g. the physical basement of this building, power infrastructure for the electric system in this building and so on.

One day, if foundation is compromised by attacker, the building would never exist no matter how secure and perfect its electric system is. Worthy to mention, there is also many ways to compromise cryptography(foundation), like cryptanalysis (take differential analysis as an example) and quantum attack (which can just make traditional cryptography unsecure by super computional power)

But in the daily life, even foundation is secure, the implementation, deployment, protocol etc of various systems in this building could still have many vulnerabilities, which would make the system operation vulnerable to attacker. For instance, if the program of elevator is compromised, although the building doesn't fall down, but attacker could make the lift stopped at a certain floor to prevent anyone in this building to use it.

These are my thoughts about cryptography and other security areas. They both are vital and necessary research areas for security, just with different ways.

The following is something irrelevant to this subject, but i will just keep this.

{% highlight go %}
func TestEncoding(t *testing.T) {
	tests := []struct {
		id   ID
		want []byte
	}{
		{ID{Hash: checksumToBytes(0), Next: 0}, common.Hex2Bytes("c6840000000080")},
		{ID{Hash: checksumToBytes(0xdeadbeef), Next: 0xBADDCAFE}, common.Hex2Bytes("ca84deadbeef84baddcafe,")},
		{ID{Hash: checksumToBytes(math.MaxUint32), Next: math.MaxUint64}, common.Hex2Bytes("ce84ffffffff88ffffffffffffffff")},
	}
	for i, tt := range tests {
		have, err := rlp.EncodeToBytes(tt.id)
		if err != nil {
			t.Errorf("test %d: failed to encode forkid: %v", i, err)
			continue
		}
		if !bytes.Equal(have, tt.want) {
			t.Errorf("test %d: RLP mismatch: have %x, want %x", i, have, tt.want)
		}
	}
}
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
