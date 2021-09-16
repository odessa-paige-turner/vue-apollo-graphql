<template>
  <div class="launch-list">
    <!-- If there is one or more queries loading -->
    <template v-if="loading > 0">
      Loading
    </template>
    <!-- Actual view -->
    <template v-else>
      <ul>
        <!-- Post list items -->
        <li v-for="launch in launchesPast" :key="launch.mission_name">
          {{ launch.mission_name }}
        </li>
      </ul>
    </template>
  </div>
</template>

<script>
import gql from 'graphql-tag';
// GraphQL query
const launchesPast = gql`
  query {
    launchesPast(limit: 10) {
      mission_name
      launch_date_local
      launch_site {
        site_name_long
      }
      links {
        article_link
        video_link
      }
      rocket {
        rocket_name
        first_stage {
          cores {
            flight
            core {
              reuse_count
              status
            }
          }
        }
        second_stage {
          payloads {
            payload_type
            payload_mass_kg
            payload_mass_lbs
          }
        }
      }
      ships {
        name
        home_port
        image
      }
    }
  }
`;
// Vue component definition
export default {
  // Local state
  data: () => ({
    // You can initialize the 'posts' data here
    launchesPast: [],
    loading: 0,
  }),
  // Apollo GraphQL
  apollo: {
    // Local state 'launches' data will be updated by the GraphQL query result
    launchesPast: {
      // GraphQL query
      query: launchesPast,
      // Will update the 'loading' attribute +1 when a new query is loading -1 when a query is completed
      loadingKey: 'loading',
    },
  },
};
</script>

<style scoped>

</style>