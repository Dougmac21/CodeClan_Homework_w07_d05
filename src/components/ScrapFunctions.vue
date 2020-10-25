    // getCompleteEpisodeData: function() {
    //   fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=0&pageSize=100&numberOfElements=100")
    //   .then(res => res.json())
    //   .then(episodes_0 => this.allEpisodes.push(this.allEpisodes, episode_0))
    //   .then(() => this.sortCompleteEpisodes("episodeNumber"));

      
      // fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=1&pageSize=100&numberOfElements=100")
      // .then(res => res.json())
      // .then(episodes_1 => this.allEpisodes.push(this.allEpisodes, episode_1))
      // .then(() => this.sortCompleteEpisodes("episodeNumber"));

      
      // fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=2&pageSize=100&numberOfElements=100")
      // .then(res => res.json())
      // .then(episodes_2 => this.allEpisodes.push(this.allEpisodes, episode_2))
      // .then(() => this.sortCompleteEpisodes("episodeNumber"));

      
      // fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=3&pageSize=100&numberOfElements=100")
      // .then(res => res.json())
      // .then(episodes_3 => this.allEpisodes.push(this.allEpisodes, episode_3))
      // .then(() => this.sortCompleteEpisodes("episodeNumber"));

      
      // fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=4&pageSize=100&numberOfElements=100")
      // .then(res => res.json())
      // .then(episodes_4 => this.allEpisodes.push(this.allEpisodes, episode_4))
      // .then(() => this.sortCompleteEpisodes("episodeNumber"));

      
      // fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=5&pageSize=100&numberOfElements=100")
      // .then(res => res.json())
      // .then(episodes_5 => this.allEpisodes.push(this.allEpisodes, episode_5))
      // .then(() => this.sortCompleteEpisodes("episodeNumber"));

      
      // fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=6&pageSize=100&numberOfElements=100")
      // .then(res => res.json())
      // .then(episodes_6 => this.allEpisodes.push(this.allEpisodes, episode_6))
      // .then(() => this.sortCompleteEpisodes("episodeNumber"));

      
      // fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=7&pageSize=100&numberOfElements=100")
      // .then(res => res.json())
      // .then(episodes_7 => this.allEpisodes.push(this.allEpisodes, episode_7))
      // .then(() => this.sortCompleteEpisodes("episodeNumber"));
    // },

    // sortCompleteEpisodes: function(episodeProperty) {
    //   this.allEpisodes.episodes.sort((episodeA, episodeB) => {
    //     return episodeA[episodeProperty] < episodeB[episodeProperty] ? -1 : 1;
    //   });
  //   }
  // },



    getEveryEpisodeData_2: function() {
      Promise.all([
        fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=$0&pageSize=100&numberOfElements=100"),
        fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=$1&pageSize=100&numberOfElements=100"),
        fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=$2&pageSize=100&numberOfElements=100"),
        fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=$3&pageSize=100&numberOfElements=100"),
        fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=$4&pageSize=100&numberOfElements=100"),
        fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=$5&pageSize=100&numberOfElements=100"),
        fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=$6&pageSize=100&numberOfElements=100"),
        fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=$7&pageSize=100&numberOfElements=100")
        ])
        .then(async([aa, bb]) => {
          const a = await aa.json();
          const b = await bb.json();
          reuturn [a, b]
        })
        .then((responseText) => {
          console.log(responseText);

        }).catch((err) => {
          console.log(err);
        });
  },
