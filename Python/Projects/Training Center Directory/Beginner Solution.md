```python
# ==========================================
# Project: Training Center Directory (Beginner-Friendly)
# ==========================================
# Goal:
# - Practice classes, inheritance, and method overriding (__repr__)
# - Build a base class (TrainingCenter) and three child classes:
#   IntroCenter, IntermediateCenter, AdvancedCenter
#
# Notes for beginners:
# - A "class" is a blueprint for creating objects.
# - "Inheritance" means a child class can reuse code from a parent class.
# - We "override" a method when a child class replaces a parent method
#   with a version that better fits the child class.
# ==========================================


class TrainingCenter:
    """Base class for all training centers (shared attributes + behavior)."""

    def __init__(self, center_name, tier, attendee_count):
        # Store basic information about the training center
        self.center_name = center_name
        self.tier = tier
        self.attendee_count = attendee_count

    # -----------------------
    # Getters (read values)
    # -----------------------
    def get_center_name(self):
        return self.center_name

    def get_tier(self):
        return self.tier

    def get_attendee_count(self):
        return self.attendee_count

    # -----------------------
    # Setter (update value)
    # -----------------------
    def set_attendee_count(self, new_count):
        # Validate: must be an integer and not negative
        if isinstance(new_count, int) and new_count >= 0:
            self.attendee_count = new_count
        else:
            print("Attendee count must be a non-negative integer.")

    # -----------------------
    # __repr__ (print-friendly summary)
    # -----------------------
    def __repr__(self):
        # When you print an object, Python uses __repr__ to show it as text
        return (
            f"{self.center_name} is an {self.tier} training center "
            f"with {self.attendee_count} attendees."
        )


class IntroCenter(TrainingCenter):
    """Child class for intro-level centers (adds a release rule)."""

    def __init__(self, center_name, attendee_count, release_rule):
        # Call the parent constructor to set shared attributes
        # tier is forced to "intro" for this type of center
        super().__init__(center_name, "intro", attendee_count)

        # Store the new attribute unique to IntroCenter
        self.release_rule = release_rule

    # Getter for the extra attribute
    def get_release_rule(self):
        return self.release_rule

    # Override __repr__ so printing includes the release rule
    def __repr__(self):
        base_info = super().__repr__()  # reuse the parent summary
        return base_info + f" Release rule: {self.release_rule}."


class IntermediateCenter(TrainingCenter):
    """Child class for intermediate centers (no extra attributes)."""

    def __init__(self, center_name, attendee_count):
        # tier is forced to "intermediate"
        super().__init__(center_name, "intermediate", attendee_count)


class AdvancedCenter(TrainingCenter):
    """Child class for advanced centers (adds a list of tracks)."""

    def __init__(self, center_name, attendee_count, tracks):
        # Call the parent constructor to set shared attributes
        # tier is forced to "advanced"
        super().__init__(center_name, "advanced", attendee_count)

        # tracks should be a list (example: ["Red Team", "Threat Hunting"])
        self.tracks = tracks

    # Getter for the extra attribute
    def get_tracks(self):
        return self.tracks

    # Override __repr__ so printing includes the tracks list
    def __repr__(self):
        base_info = super().__repr__()  # reuse the parent summary

        # Turn the list into a readable string:
        # ["A", "B", "C"] -> "A, B, C"
        track_list = ", ".join(self.tracks)

        return base_info + f" Available tracks: {track_list}."


# ==========================================
# Quick Tests (run this file to see output)
# ==========================================

# Create a basic TrainingCenter (uses base class directly)
basic = TrainingCenter("Downtown Hub", "intermediate", 20)
print(basic)

# Use getters
print("Name:", basic.get_center_name())
print("Tier:", basic.get_tier())
print("Attendees:", basic.get_attendee_count())

# Use setter (with validation)
basic.set_attendee_count(25)     # valid
basic.set_attendee_count(-5)     # invalid
basic.set_attendee_count("lots") # invalid
print("Updated:", basic)

print("\n---\n")

# Create an IntroCenter (child class)
intro = IntroCenter("Welcome Center", 15, "Release after 4 PM to approved contacts")
print(intro)
print("Release rule:", intro.get_release_rule())

print("\n---\n")

# Create an IntermediateCenter (child class with no extras)
mid = IntermediateCenter("Skills Workshop", 30)
print(mid)

print("\n---\n")

# Create an AdvancedCenter (child class)
advanced = AdvancedCenter("Ops Lab", 10, ["Security Ops", "Threat Analysis"])
print(advanced)
print("Tracks:", advanced.get_tracks())

# Update attendee count via setter inherited from TrainingCenter
advanced.set_attendee_count(12)
print("Updated:", advanced)
```
