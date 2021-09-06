# assignment2-guntupalli
Hi, I am G. Mounisha. I got familiar with Git and it's commands. 

# Mounisha Guntupalli
###### My favourite place is Greece.

Greece is famous for its amazing **beaches and clear-blue waters**. In addition, it has the perfect beauty of Cycladic architecture, incredible sunset spots, and warm summer weather whihch makes it one of **Europe's most popular vacation destinations**.

---

# Directions from Maryville to Greece
1. Take a cab from Maryville to Kansas City International Airport (MCI)
2. Kansas City International Airport (MCI) to Dulles International Airport (IAD)
   1. Complete your check-in process in kansas
   2. Board your flight
   3. Wait for your connecting flight
3. Dulles International Airport (IAD) to Athens International Airport (ATH)
   1. Board the flight from Virgina to Greece
   2. Complete your check-out process in greece
4. Athens International Airport (ATH) to Coco-Mat Athens BC (Hotel)

* Beautiful dresses
* Lots of Money 
* Cosmetics
  * Make-up
  * Moisturizer and sun screen
* Choclates and snacks

[Click here for AboutMe](https://github.com/mounishaS545235/assignment2-guntupalli/blob/main/AboutMe.md)


---

# Food/Drinks that I would recommend to others

I am a foodie and I like trying new flavours and drinks. Every weekend I like to visit new places with my friends and cousins. So, below are the food/drinks items that I like my friends to try and love them. 

| Food                              | Location       | Price |
| ---                               | ---            | ---:  |
| Hot Nutella lava cake             | Madhapur       | $15   |
| Drumstick Donne Biryani           | Kondapur       | $21   |
| WoodFried Poasted chicken Pizza   | Jubliee hills  | $20   |
| Blueberry cheese Shake            | Nagole         | $12   |


---

# Inspirational Quotes by Great People

> " *When our signature changes to autograph, this marks the success.* "
>      - by ***Abdul Kalam***
>      
> " *If you judge people, you have no time to love them.* "
>      - by ***Mother Teresa***


---

# Minkowski Sum Definition and source code

> Let P and Q be two point sets in Rpow(d). The Minkowski sum of P and Q, denoted as P ⊕ Q, is the point set {p + q | p ∈ P, q ∈ Q}. Applies to every dimension d. Applies to arbitrary point sets.

Source link for Definition - <http://acg.cs.tau.ac.il/courses/algorithmic-robotics/spring-2011/slides/ms.pdf>

```
struct pt{
    long long x, y;
    pt operator + (const pt & p) const {
        return pt{x + p.x, y + p.y};
    }
    pt operator - (const pt & p) const {
        return pt{x - p.x, y - p.y};
    }
    long long cross(const pt & p) const {
        return x * p.y - y * p.x;
    }
};

void reorder_polygon(vector<pt> & P){
    size_t pos = 0;
    for(size_t i = 1; i < P.size(); i++){
        if(P[i].y < P[pos].y || (P[i].y == P[pos].y && P[i].x < P[pos].x))
            pos = i;
    }
    rotate(P.begin(), P.begin() + pos, P.end());
}

vector<pt> minkowski(vector<pt> P, vector<pt> Q){
    // the first vertex must be the lowest
    reorder_polygon(P);
    reorder_polygon(Q);
    // we must ensure cyclic indexing
    P.push_back(P[0]);
    P.push_back(P[1]);
    Q.push_back(Q[0]);
    Q.push_back(Q[1]);
    // main part
    vector<pt> result;
    size_t i = 0, j = 0;
    while(i < P.size() - 2 || j < Q.size() - 2){
        result.push_back(P[i] + Q[j]);
        auto cross = (P[i + 1] - P[i]).cross(Q[j + 1] - Q[j]);
        if(cross >= 0)
            ++i;
        if(cross <= 0)
            ++j;
    }
    return result;
}
```

Source link for code - <https://cp-algorithms.com/geometry/minkowski.html>